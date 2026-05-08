# RMF Compliance Vault — Operating Manual

This vault is a two-tier compliance knowledge base. You (Claude Code) are the primary author and maintainer. All content uses **Obsidian Flavored Markdown** — wikilinks, callouts, embeds, and typed properties.

Obsidian syntax reference is available at `.claude/obsidian-skills/skills/obsidian-markdown/`.

## Architecture

### Tier 1: Sources (Read-Only)
`Sources/` contains authoritative policy text — NIST publications, OWASP standards, FedRAMP baselines. These are ground truth.

**Rules:**
- NEVER modify, summarize, or paraphrase files under `Sources/`.
- Always cite and defer to source text when answering compliance questions.
- When quoting source text, use `> [!quote]` callouts with a wikilink to the source file and section:
  ```markdown
  > [!quote] NIST 800-53 AC-2
  > "The organization manages information system accounts..."
  > — [[Sources/NIST-800-53/AC-access-control#AC-2 Account Management|AC-2]]
  ```

### Tier 2: Wiki (LLM-Maintained)
`Wiki/` contains your articles — narratives, patterns, implementation guidance, cross-framework mappings, decision records, and filed Q&A outputs.

**Rules:**
- You own this structure. Create, rename, move, merge, and split notes freely.
- Create directories when a topic area accumulates 3+ notes.
- Every article that references a control or requirement MUST use a `> [!quote]` callout with a `[[wikilink]]` to the specific source passage in `Sources/`.
- If no source exists yet, use: `> [!danger] NEEDS SOURCE: <control ID>`
- Use typed YAML frontmatter with `sources` and `related` as link properties (see Frontmatter section).

## Obsidian Syntax Rules

### Always use wikilinks for internal references

```markdown
[[least-privilege-implementation]]                          # wiki note
[[Sources/NIST-800-53/AC-access-control#AC-2|AC-2]]        # source heading with display text
![[Sources/NIST-800-53/AC-access-control#AC-2]]             # embed source content inline
```

**Never** use standard markdown links `[text](path.md)` for internal vault files.

### Callout types for compliance signals

| Callout | Use For | Example |
|---|---|---|
| `> [!quote]` | Verbatim source citations | Policy language from Sources/ |
| `> [!danger]` | Missing sources, compliance gaps | `NEEDS SOURCE` tags |
| `> [!warning]` | Citation drift, stale content | Wiki/Source conflicts |
| `> [!example]` | Implementation patterns | AWS, Azure, GCP examples |
| `> [!info]` | Cross-framework mappings | Control equivalences |
| `> [!tip]` | Best practices | Recommendations |
| `> [!abstract]` | Executive summaries | Top of long articles |

Use `-` suffix for foldable (collapsed by default): `> [!quote]- Full Control Text`

### Tags

Use hierarchical tags for fine-grained categorization:
```yaml
tags:
  - access-control/account-management
  - fedramp/moderate
  - implementation/aws
```

## Vault Layout

```
Sources/          # Tier 1: Authoritative, read-only
  NIST-800-53/
  FedRAMP/
  NIST-AI-RMF/
  OWASP-LLM/
  NIST-800-171/
  _index.md       # Ingestion status tracker

Wiki/             # Tier 2: LLM-maintained articles
  _index.md       # Auto-maintained master index

Capture/          # Inbox for unprocessed raw material
  archived/       # Processed captures moved here

Templates/        # Frontmatter conventions
Attachments/      # Images, diagrams
.claude/          # Obsidian skills (obsidian-markdown, obsidian-bases, etc.)
```

## Workflows

### Answering Questions
1. Read the relevant Wiki article(s) first for context.
2. Verify against `Sources/` before responding — if there's a conflict, Sources wins.
3. Update the Wiki article if it has drifted (flag with `> [!warning] Citation Drift`).
4. Include both practical guidance AND source citations in your response.
5. If the answer adds new knowledge, file it as a new or updated Wiki article with proper frontmatter and wikilinks.

### Capture → Compile
1. Read everything in `Capture/` (raw material: web clips, notes, PDFs, copy-paste).
2. For each piece of content:
   - Identify which framework(s) it relates to.
   - Create or update Wiki articles with synthesized content.
   - Cite sources using `> [!quote]` callouts with `[[wikilinks]]` to `Sources/` files.
   - If no source exists, mark with `> [!danger] NEEDS SOURCE`.
   - Add `[[wikilinks]]` to related Wiki articles.
   - Set `sources:` and `related:` link properties in frontmatter.
3. Move processed files to `Capture/archived/`.
4. Regenerate all `_index.md` files and `VAULT-INDEX.md`.

### Project Integration
When generating compliance artifacts (SSPs, control implementations, policies):
- Pull control language **verbatim** from `Sources/` using `> [!quote]` callouts.
- Add implementation narrative and guidance from `Wiki/`.
- Cite both the source and any relevant Wiki patterns via `[[wikilinks]]`.

### Lint / Health Check
When asked to lint or run a health check:
- Find orphan notes (no incoming `[[wikilinks]]` from other notes).
- Find Wiki articles whose `> [!quote]` citations have drifted from source text.
- Identify missing cross-references between frameworks.
- Suggest gap areas (frameworks/controls with no Wiki coverage).
- Flag standard markdown links used instead of wikilinks.
- Fix inconsistent or missing frontmatter.
- Report stats: total notes, notes per framework, orphan count, last updated dates.

## Index Maintenance

Regenerate indexes after every session that changes content:

### VAULT-INDEX.md (root)
Master index listing all Wiki articles grouped by topic, with one-line summaries. Also lists Sources ingestion status.

### _index.md (per-directory)
Local index for any directory with 2+ files. One line per file with a brief description.

**Format:**
```markdown
- [[filename]] — one-line description
```

## Frontmatter Conventions

All Wiki notes use YAML frontmatter with Obsidian-typed properties:

```yaml
---
type: concept
framework: nist-800-53
status: draft
tags:
  - access-control
  - least-privilege
created: 2026-04-05
updated: 2026-04-05
sources:
  - "[[Sources/NIST-800-53/AC-access-control]]"
  - "[[Sources/FedRAMP/fedramp-moderate-baseline]]"
related:
  - "[[Wiki/fedramp-moderate-access-controls]]"
---
```

### Property types

| Property | Obsidian Type | Notes |
|---|---|---|
| `type` | text | concept, pattern, decision-record, mapping, guide, session-log |
| `framework` | text | nist-800-53, fedramp, nist-ai-rmf, owasp-llm, nist-800-171, cross-framework |
| `status` | text | draft, review, final |
| `tags` | list | Freeform, hierarchical (e.g., `access-control/least-privilege`) |
| `created` | date | YYYY-MM-DD |
| `updated` | date | YYYY-MM-DD |
| `sources` | links | Wikilinks to Sources/ files — visible in graph view |
| `related` | links | Wikilinks to other Wiki articles — visible in graph view |

Types and tags are guidance, not rigid gates. Adapt as content demands.

## File Naming

- Kebab-case: `least-privilege-implementation.md`
- Atomic: one concept per note
- Descriptive: filename communicates content without opening
- Wikilink-friendly: avoid special characters that break `[[links]]`
- Prefer flat/shallow over deep nesting

## Relationship to Skills

| Resource | Use For |
|---|---|
| `/rmf-vault` skill | Compile, query, lint, index, status, ingest operations |
| `/nist-800-53` skill | Quick control lookups, AWS Config rules, project generation |
| `/fedramp` skill | Baseline checks, AWS compliance rules, FedRAMP project generation |
| `/nist-ai-rmf` skill | Subcategory lookups, gap analysis, AI RMF project generation |
| This vault — Sources/ | Authoritative full-text policy language, verbatim control descriptions |
| This vault — Wiki/ | Narratives, implementation patterns, cross-framework mappings, decision records |

## Search Patterns

When searching the vault from other working directories, use the full path:
```
Grep: pattern="AC-2" path="C:/Users/samue/OneDrive/Obsidian/rmf_obsidian/Sources/"
Glob: pattern="**/_index.md" path="C:/Users/samue/OneDrive/Obsidian/rmf_obsidian/"
```
