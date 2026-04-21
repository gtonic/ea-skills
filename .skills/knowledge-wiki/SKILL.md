---
name: knowledge-wiki
description: "Knowledge management skill implementing the Raw/Wiki/Outputs pattern (inspired by Karpathy's LLM Wiki). Three modes: Ingest (add new sources to raw/, create wiki annotations), Lint (verify cross-references, detect stale links, check raw/ immutability), Reindex (rebuild index.md catalog and log.md audit trail). Triggers include 'ingest document', 'add source', 'wiki annotation', 'lint wiki', 'check references', 'reindex', 'rebuild index', 'update index', 'knowledge base', 'wiki update', 'add to sources', 'new source material', 'companion file', 'wiki.md', 'source classification', 'link check', 'stale references', 'index.md', 'log.md', 'knowledge audit'. Target audience: Enterprise Architects maintaining the monorepo knowledge base."
---

# Knowledge Wiki — Raw/Wiki/Outputs Management

Maintain the monorepo as a structured knowledge base with clear separation between
immutable source materials (`raw/`) and synthesized wiki content (`wiki/`).
Generated artifacts live in `outputs/`, standalone tools in `products/`.

Inspired by the **LLM Wiki pattern** (Karpathy): Raw Sources → Wiki → Schema,
with three operations: Ingest, Query (via index), and Lint.

---

## MANDATORY: Entry-Point Dialog

**Before any action**, present the mode selection:

> **Which knowledge management activity do you want to perform?**
>
> 1. **Ingest** — Add a new source document to `raw/`, classify it,
>    and optionally create a wiki annotation (`.wiki.md` companion file)
> 2. **Lint** — Verify cross-references, detect broken links, check that
>    `raw/` files haven't been modified, find orphaned documents
> 3. **Reindex** — Rebuild `index.md` (content catalog) and append to
>    `log.md` (chronological audit trail)
>
> Choose **1**, **2**, or **3** (or a combination, e.g. "1 and 3").

### Rules

- **Never skip.** Even if the user prompt hints at a mode, always confirm first.
- **Execute only after selection** — then follow the matching workflow below.
- **Combinations allowed.** E.g. "1 and 3" → run Ingest, then Reindex.

---

## Mode 1 — Ingest

Add a new source document to the knowledge base.

### Step 1: Classify the Source

Ask the user to provide the document (file path, URL, or pasted content).
Then classify into one of four categories:

| Category | Target Directory | Criteria |
|----------|-----------------|----------|
| **standards** | `raw/standards/` | Industry frameworks, reference models, governance standards (TOGAF, ISO, IIA, RAMI) |
| **templates** | `raw/templates/` | Reusable document templates, schemas, checklists |
| **reference** | `raw/reference/` | Technical reference docs, vendor evaluations, tool guides |
| **books** | `raw/books/` | PDF books, long-form publications |
| **data** | `raw/data/` | Reference JSON data sets, example portfolios |

Present the classification to the user for confirmation before proceeding.

### Step 2: Normalize and Place

1. **Normalize filename**: Replace spaces with underscores, keep original extension
2. **Move/copy** to the appropriate `raw/<category>/` directory
3. **Verify** the file landed correctly

### Step 3: Optional Wiki Annotation

Ask the user:

> Do you want to create a **wiki annotation** (`.wiki.md` companion file)?
> This captures your interpretation, summary, or notes about this source.
>
> If yes, which folder should the annotation live in?
> (e.g., `wiki/StrategischeBebauung/`, `wiki/AI_Governance/`, or suggest one)

If yes, create a companion file using this template:

```markdown
# <Title> — Wiki Annotation

> Source: [`raw/<category>/<filename>`](../../raw/<category>/<filename>)
> Ingested: <YYYY-MM-DD>
> Classification: <category>

## Summary

<2-3 sentence summary of the source>

## Key Takeaways for EA Context

- <Bullet points relevant to the Doppelmayr EA context>

## Cross-References

- Related to: [<linked wiki page>](<path>)
```

### Step 4: Update Tracking

1. **Append** an entry to `log.md`:
   ```
   | <YYYY-MM-DD> | INGEST | `raw/<category>/<filename>` | <one-line description> |
   ```
2. **Offer** to run Reindex (Mode 3) to update `index.md`

### Follow-Up after Ingest

> Next steps:
> - **A)** Ingest another source document
> - **B)** Create a wiki annotation for an existing source
> - **C)** Run **Reindex** to update `index.md`
> - **D)** Run **Lint** to verify all cross-references

---

## Mode 2 — Lint

Verify structural integrity of the knowledge base.

### Checks to Run (in order)

#### Check 1: Broken Internal Links
Scan all `.md` files for markdown links `[text](path)` and verify each target exists.
Report as a table:

| File | Line | Broken Link | Suggestion |
|------|------|-------------|------------|

#### Check 2: raw/ Immutability
Compare `raw/` file list against `index.md` entries.
Flag any files in `raw/` that are **not listed** in `index.md` (untracked sources).

#### Check 3: Orphaned Wiki Annotations
Find `.wiki.md` files whose referenced source in `raw/` no longer exists.

#### Check 4: Cross-Reference Consistency
For files in `REPOSITORY_OVERVIEW.md` that reference moved directories
(02_DM_Prep, 10_OT, 40_IFS, 50_ThreeLines), verify they now point to `raw/`.

#### Check 5: Stale Directory References
Search for links to directories that no longer exist (old numbered prefixes like `00_`, `03_`, etc., or old `_sources/` paths that were not updated to `raw/`). Report and suggest fixes.

### Output Format

```
## Lint Report — <YYYY-MM-DD>

### ✅ Passed Checks
- <check name>: <count> items verified

### ⚠️ Warnings
- <check name>: <details>

### ❌ Errors
- <check name>: <details with fix suggestions>

### Summary
- Files scanned: <n>
- Links checked: <n>
- Issues found: <n> (errors: <n>, warnings: <n>)
```

### Follow-Up after Lint

> Next steps:
> - **A)** Auto-fix broken links (where a clear fix is available)
> - **B)** Run **Reindex** to synchronize `index.md`
> - **C)** Review and fix issues manually
> - **D)** Re-run Lint to verify fixes

---

## Mode 3 — Reindex

Rebuild `index.md` and update `log.md`.

### Step 1: Scan Repository

Walk the full directory tree and classify every document:

| Zone | Directories | Description |
|------|-------------|-------------|
| **Raw** | `raw/**` | Immutable source materials |
| **Wiki** | `wiki/**` | Synthesized wiki content |
| **Outputs** | `outputs/**` | Generated artifacts (.pptx, .pdf, .docx) |
| **Products** | `products/**` | Standalone tools (ea-dashboard, dm-presentation, PageIndex) |
| **Data** | `raw/data/`, `wiki/*/portfolio.json`, `products/ea-dashboard/app/data/` | Structured data files |
| **Root** | `*.md`, `*.py` at root | Architecture docs, scripts, meta-files |

### Step 2: Rebuild index.md

Generate `index.md` using this structure:

```markdown
# Repository Index

> Auto-generated by knowledge-wiki skill. Last updated: <YYYY-MM-DD>

## Raw — Immutable Sources (`raw/`)

| File | Category | Description |
|------|----------|-------------|
| [<filename>](raw/<cat>/<file>) | <category> | <one-line description> |

## Wiki Content

### <Folder Name> — <Topic>
| File | Description | Sources Referenced |
|------|-------------|-------------------|
| [<filename>](wiki/<folder>/<file>) | <description> | <links to raw/ if any> |

## Zone C — Structured Data
...

## Zone D — Tooling & Generators
...
```

### Step 3: Update log.md

Append a REINDEX entry:

```
| <YYYY-MM-DD> | REINDEX | Full repository scan | <n> files indexed, <n> sources, <n> wiki pages |
```

### Follow-Up after Reindex

> Next steps:
> - **A)** Run **Lint** to verify the freshly generated index
> - **B)** Review `index.md` and suggest improvements
> - **C)** Ingest a new source document

---

## Key Conventions

### File Organization Rules

1. **`raw/`** is the ONLY location for immutable source materials
2. Files in `raw/` are NEVER edited — only added or (rarely) removed
3. Wiki annotations use the `.wiki.md` suffix and live in the `wiki/` folders
4. `index.md` is auto-generated — manual edits will be overwritten by Reindex
5. `log.md` is append-only — never edit existing entries
6. Generated artifacts (.pptx, .pdf, .docx) belong in `outputs/`
7. Standalone products live in `products/`

### Filename Conventions

- Replace spaces with underscores in `raw/`
- Keep original file extensions
- PDFs go to `raw/books/` regardless of size

### Link Conventions

- Use standard markdown links `[text](relative/path)` (not `[[wikilinks]]`)
- Relative paths from the linking file's location
- Cross-reference `raw/` files from wiki pages, never the reverse

### REPOSITORY_OVERVIEW.md

This file is the **meta-overview** of the repository structure. When Reindex runs:
- Verify the layout table includes `raw/`, `wiki/`, `outputs/`, `products/`
- Verify old moved directories show redirect notes
- Do NOT auto-modify REPOSITORY_OVERVIEW.md — flag inconsistencies for the user instead
