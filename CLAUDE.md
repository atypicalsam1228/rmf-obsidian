# RMF Compliance Vault — Operating Manual

This vault is a two-tier compliance knowledge base. You (Claude Code) are the primary author and maintainer.

## Architecture

### Tier 1: Sources (Read-Only)
`Sources/` contains authoritative policy text — NIST publications, OWASP standards, FedRAMP baselines. These are ground truth.

**Rules:**
- NEVER modify, summarize, or paraphrase files under `Sources/`.
- Always cite and defer to source text when answering compliance questions.
- When quoting source text, use blockquotes (`>`) with a link to the source file and section.

### Tier 2: Wiki (LLM-Maintained)
`Wiki/` contains your articles — narratives, patterns, implementation guidance, cross-framework mappings, decision records, and filed Q&A outputs.

**Rules:**
- You own this structure. Create, rename, move, merge, and split notes freely.
- Create directories when a topic area accumulates 3+ notes.
- Every article that references a control or requirement MUST link to the specific source passage in `Sources/`.
- Use consistent YAML frontmatter (see Templates/) but choose tags and categories as content demands.

## Vault Layout

```
Sources/          # Tier 1: Authoritative, read-only
  NIST-800-53/    # Control families (AC, AU, CM, etc.)
  FedRAMP/        # Baseline documents and deltas
  NIST-AI-RMF/    # Govern/Map/Measure/Manage
  OWASP-LLM/      # LLM Top 10 risks
  NIST-800-171/   # CUI protection requirements
  _index.md       # Ingestion status tracker

Wiki/             # Tier 2: LLM-maintained articles
  _index.md       # Auto-maintained master index

Capture/          # Inbox for unprocessed raw material
  archived/       # Processed captures moved here

Templates/        # Frontmatter conventions
Attachments/      # Images, diagrams
```

## Workflows

### Answering Questions
1. Read the relevant Wiki article(s) first for context.
2. Verify against `Sources/` before responding — if there's a conflict, Sources wins.
3. Update the Wiki article if it has drifted from the source.
4. Include both practical guidance AND source citations in your response.
5. If the answer adds new knowledge to the vault, file it as a new or updated Wiki article.

### Capture → Compile
1. Read everything in `Capture/` (raw material: web clips, notes, PDFs, copy-paste).
2. For each piece of content:
   - Identify which framework(s) it relates to.
   - Create or update Wiki articles with synthesized content.
   - Link to specific passages in `Sources/` — extract direct quotes using blockquotes rather than paraphrasing.
   - Add backlinks to related Wiki articles.
3. Move processed files to `Capture/archived/`.
4. Regenerate all `_index.md` files and `VAULT-INDEX.md`.

### Project Integration
When generating compliance artifacts (SSPs, control implementations, policies):
- Pull control language **verbatim** from `Sources/`.
- Add implementation narrative and guidance from `Wiki/`.
- Cite both the source and any relevant Wiki patterns.

### Lint / Health Check
When asked to lint or run a health check:
- Find orphan notes (no incoming links from other notes).
- Find Wiki articles whose citations have drifted from source text.
- Identify missing cross-references between frameworks.
- Suggest gap areas (frameworks/controls with no Wiki coverage).
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
- [Note Title](filename.md) — one-line description
```

## Frontmatter Conventions

All Wiki notes should include YAML frontmatter:
```yaml
---
type: # concept | pattern | decision-record | mapping | guide | session-log
framework: # nist-800-53 | fedramp | nist-ai-rmf | owasp-llm | nist-800-171 | cross-framework
status: # draft | review | final
tags: []
created: YYYY-MM-DD
updated: YYYY-MM-DD
---
```

Types and tags are guidance, not rigid gates. Adapt as content demands.

## File Naming

- Kebab-case: `least-privilege-implementation.md`
- Atomic: one concept per note
- Descriptive: the filename should tell you the content without opening it
- Prefer flat/shallow over deep nesting

## Relationship to Skills

| Resource | Use For |
|---|---|
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
