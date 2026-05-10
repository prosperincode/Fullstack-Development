# LLM Wiki Schema

This vault follows the LLM Wiki pattern from Andrej Karpathy's guide: raw sources are immutable, the wiki is LLM-maintained markdown, and this file is the operating schema for Codex.

## Layers

- `raw/` contains source documents curated by the user. Read from this folder, but do not modify files in it unless the user explicitly asks.
- `wiki/` contains generated markdown pages. Codex owns this layer: create, update, cross-reference, and keep pages consistent.
- `AGENTS.md` defines the structure and workflows for maintaining the wiki.

## Wiki Structure

- `wiki/index.md` is the content-oriented catalog. Read it first when answering questions or deciding what pages to update.
- `wiki/log.md` is the append-only chronological record of ingests, queries, and lint passes.
- `wiki/sources/` contains source summary pages.
- `wiki/entities/` contains entity pages.
- `wiki/concepts/` contains concept pages.
- `wiki/comparisons/` contains comparison or synthesis pages created from queries.
- `wiki/overview.md` is the high-level overview of the wiki.
- `wiki/synthesis.md` is the evolving synthesis across sources and questions.

## Ingest Workflow

1. Read the new source from `raw/`.
2. Discuss key takeaways with the user when emphasis or interpretation is unclear.
3. Write or update the relevant source summary in `wiki/sources/`.
4. Update relevant entity, concept, overview, synthesis, or comparison pages.
5. Update `wiki/index.md`.
6. Append an entry to `wiki/log.md` using `## [YYYY-MM-DD] ingest | Source Title`.

## Query Workflow

1. Read `wiki/index.md`.
2. Read the relevant wiki pages.
3. Synthesize the answer with citations to wiki pages and source pages.
4. When the answer is durable, file it back into the wiki as a new or updated page.
5. Append an entry to `wiki/log.md` using `## [YYYY-MM-DD] query | Question or Topic`.

## Lint Workflow

Periodically inspect the wiki for contradictions, stale claims, orphan pages, missing cross-references, important concepts without pages, and data gaps that need new sources.

Append lint results to `wiki/log.md` using `## [YYYY-MM-DD] lint | Scope`.
