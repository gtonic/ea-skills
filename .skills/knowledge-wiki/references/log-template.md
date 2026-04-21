# Knowledge Base Change Log

> Append-only audit trail for the monorepo knowledge base.
> Each entry records a knowledge management operation.

| Date | Operation | Target | Description |
|------|-----------|--------|-------------|
| <YYYY-MM-DD> | INGEST | `raw/<category>/<file>` | <one-line description of what was added> |
| <YYYY-MM-DD> | LINT | Full scan | <summary: n files scanned, n issues found> |
| <YYYY-MM-DD> | REINDEX | `index.md` | <n files indexed, n sources, n wiki pages> |
| <YYYY-MM-DD> | MOVE | `<old-path>` → `<new-path>` | <reason for restructuring> |
| <YYYY-MM-DD> | DELETE | `raw/<category>/<file>` | <reason for removal> |
