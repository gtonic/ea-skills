# Knowledge Wiki Skill

Maintain the monorepo as a structured knowledge base with clear separation between
immutable source materials and synthesized wiki content.

## Purpose

This skill implements the **Raw/Wiki/Schema** pattern for knowledge management,
ensuring that source materials (standards, templates, reference docs, books) are
cleanly separated from your synthesized analysis, summaries, and architecture decisions.

## When to Use

Use this skill when you need to:

- Add new source documents to the knowledge base
- Create wiki annotations for existing sources
- Verify cross-references and detect broken links
- Rebuild the repository index after changes
- Audit the knowledge base for consistency
- Classify documents as sources vs. wiki content

**Trigger phrases**: "ingest document", "add source", "wiki annotation", "lint wiki",
"check references", "reindex", "rebuild index", "update index", "knowledge base",
"wiki update", "add to sources", "new source material", "companion file"

## How It Works

The skill offers three modes:

1. **Ingest** — Classify a new document, place it in `raw/<category>/`,
   optionally create a `.wiki.md` companion annotation
2. **Lint** — Scan all markdown files for broken links, verify `raw/`
   immutability, find orphaned annotations, check cross-reference consistency
3. **Reindex** — Rebuild `index.md` (zone-based content catalog) and append
   audit entries to `log.md`

## Architecture

```
raw/                         ← Immutable source materials
├── standards/               ← Industry frameworks, reference models
├── templates/               ← Reusable templates and schemas
├── reference/               ← Technical docs, evaluations
├── books/                   ← PDF books and publications
└── data/                    ← Reference JSON data sets

wiki/                        ← Synthesized wiki content
├── EA_Vorarlberg/           ← EA Frameworks, KI-Reifegrad
├── StrategischeBebauung/    ← 10-Domänen-Capability-Modell
└── .../                     ← etc.

outputs/                     ← Generated artifacts (.pptx, .pdf)
products/                    ← Standalone tools (ea-dashboard, etc.)

index.md                     ← Auto-generated content catalog
log.md                       ← Append-only audit trail
```

## Companion File Convention

For any source `raw/standards/Foo.md`, a wiki annotation lives at:
```
<wiki-folder>/Foo.wiki.md
```
The `.wiki.md` suffix signals "this is our interpretation of an immutable source."
