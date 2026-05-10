# LLM Wiki Schema

This vault follows the LLM Wiki pattern from Andrej Karpathy's guide: raw sources are immutable, the wiki is LLM-maintained markdown, and this file is the operating schema for Codex.

The domain of this wiki is software development notes: web development, Next.js, React Native, JavaScript, TypeScript, CSS, HTML, AI-assisted development workflows, and adjacent engineering topics.

## Layers

- `raw/` contains source documents curated by the user. Read from this folder, but do not modify files in it unless the user explicitly asks.
- `raw/processed/` contains source documents that have already been ingested.
- `wiki/` contains generated markdown pages. Codex owns this layer: create, update, cross-reference, and keep pages consistent.
- `AGENTS.md` defines the structure and workflows for maintaining the wiki.

## Wiki Structure

- `wiki/index.md` is the content-oriented catalog. Read it first when answering questions or deciding what pages to update.
- `wiki/log.md` is the append-only chronological record of ingests, queries, and lint passes.
- `wiki/sources/` contains source summary pages for ingested clippings and other raw materials.
- Other wiki pages are categorized by development topic. Use clear category folders such as `wiki/Mobile Development/React Native/Expo/`, `wiki/Web Development/Next.js/`, `wiki/Languages/TypeScript/`, or `wiki/AI-Assisted Development/` when the content calls for them.
- Create category folders only when needed by ingested sources or durable query results.

## Verification and Enrichment

- Before processing any clipping, check the web for current, authoritative information related to the clipping's claims.
- Prefer official documentation and primary sources for technical facts: framework docs, platform docs, language specs, standards, vendor docs, release notes, and official pricing pages.
- If the clipping is outdated, incomplete, or contradicted by current sources, note the update in the wiki page and synthesize the corrected version.
- You may add relevant information beyond the clipping when it improves accuracy or understanding, but keep it tied to the clipping's topic.
- Include source links for both the original clipping and the web sources used for verification.
- Treat model rankings, prices, product limits, and tool capabilities as volatile; verify them at ingest time.

## Explanation Standards

- Include code examples when they make implementation details clearer.
- Include tables when they help compare concepts, commands, artifacts, tradeoffs, or platform behavior.
- Include PlantUML code blocks when sequence, architecture, lifecycle, or decision flow diagrams improve understanding.
- Use concise explanations and cross-link related wiki pages with Obsidian links.

## Ingest Workflow

1. Read the new source from `raw/`.
2. Verify the source's technical claims against current web sources before writing wiki content.
3. Discuss key takeaways with the user when emphasis or interpretation is unclear.
4. Write or update the relevant source summary page in `wiki/sources/`.
5. Update relevant categorized wiki pages.
6. Update `wiki/index.md`.
7. Move the ingested raw source to `raw/processed/`.
8. Append an entry to `wiki/log.md` using `## [YYYY-MM-DD] ingest | Source Title`.

## Query Workflow

1. Read `wiki/index.md`.
2. Read the relevant wiki pages.
3. Synthesize the answer with citations to wiki pages and source pages.
4. When the answer is durable, file it back into the wiki as a new or updated page.
5. Append an entry to `wiki/log.md` using `## [YYYY-MM-DD] query | Question or Topic`.

## Lint Workflow

Periodically inspect the wiki for contradictions, stale claims, orphan pages, missing cross-references, important concepts without pages, and data gaps that need new sources.

Append lint results to `wiki/log.md` using `## [YYYY-MM-DD] lint | Scope`.
