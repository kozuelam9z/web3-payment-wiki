# Wiki Schema

## Domain
Web3/payment intelligence, AI research, startup analysis, personal knowledge.
Covers: blockchain protocols, DeFi/CeFi payments, venture capital, AI/ML systems, founder insights, market analysis, and interdisciplinary synthesis.

## Conventions
- File names: lowercase, hyphens, no spaces (e.g., `stablecoin-merchant-adoption.md`)
- Every wiki page starts with YAML frontmatter (see below)
- Use `[[wikilinks]]` to link between pages (minimum 2 outbound links per page)
- When updating a page, always bump the `updated` date
- Every new page must be added to `index.md` under the correct section
- Every action must be appended to `log.md`
- **Provenance markers:** On pages that synthesize 3+ sources, append `^[raw/articles/source-file.md]`
  at the end of paragraphs whose claims come from a specific source. This lets a reader trace each
  claim back without re-reading the whole raw file. Optional on single-source pages where the
  `sources:` frontmatter is enough.
- **Chinese source:** Write summary, analysis, and wiki pages in Chinese. Add a `## English Summary`
  section at the end with English translation.
- **English source:** Write in English first. Then append a `## 中文摘要` section with Chinese translation/summary.

## Frontmatter (Wiki Pages)

```yaml
---
title: Page Title
created: YYYY-MM-DD
updated: YYYY-MM-DD
type: entity | concept | comparison | query | summary
tags: [from taxonomy below]
sources: [raw/articles/source-name.md, raw/papers/paper-name.pdf]
# Optional quality signals:
confidence: high | medium | low
contested: true
contradictions: [other-page-slug]
---
```

## Frontmatter (Raw Sources)

```yaml
---
source_url: https://example.com/article
ingested: YYYY-MM-DD
sha256: <hex digest of body content only>
---
```

## Tag Taxonomy

### Topics
- `web3` — blockchain, DeFi, CeFi, protocol design, tokenomics
- `payment` — stablecoin payments, merchant adoption,收单, settlement, cross-border
- `ai-ml` — AI/ML research, models, benchmarks, training, inference
- `startup` — venture capital, founder strategy, fundraising, growth
- `personal` — personal knowledge, notes, reflections, life learning

### Entity Types
- `person` — notable individuals (founders, researchers, investors)
- `company` — companies, protocols, protocols, projects
- `product` — specific products, tools, platforms
- `lab` — research labs, open-source organizations

### Content Types
- `concept` — theories, frameworks, mental models
- `comparison` — side-by-side analyses, benchmarks
- `query` — filed Q&A, answered questions worth preserving
- `summary` — synthesized insights from multiple sources
- `raw` — immutable source material (in raw/)

### Quality Signals
- `high-confidence` — well-supported across multiple sources
- `contested` — contradictory claims in literature
- `stale` — needs updating (>90 days since last review)

### Source Types
- `article` — web article, blog post
- `wechat` — WeChat public account article
- `paper` — academic paper, research report
- `pdf` — PDF document
- `telegram` — Telegram message or group content
- `transcript` — meeting notes, interview transcript, podcast
- `image` — screenshot, diagram, visual content

## Page Thresholds
- **Create a page** when an entity/concept appears in 2+ sources OR is central to one source
- **Add to existing page** when a source mentions something already covered
- **DON'T create a page** for passing mentions, minor details, or things outside the domain
- **Split a page** when it exceeds ~200 lines — break into sub-topics with cross-links
- **Archive a page** when fully superseded — move to `_archive/`, remove from index

## Entity Pages
One page per notable entity. Include:
- Overview / what it is
- Key facts and dates
- Relationships to other entities ([[wikilinks]])
- Source references

## Concept Pages
One page per concept or topic. Include:
- Definition / explanation
- Current state of knowledge
- Open questions or debates
- Related concepts ([[wikilinks]])

## Comparison Pages
Side-by-side analyses. Include:
- What is being compared and why
- Dimensions of comparison (table format preferred)
- Verdict or synthesis
- Sources

## Update Policy
When new information conflicts with existing content:
1. Check the dates — newer sources generally supersede older ones
2. If genuinely contradictory, note both positions with dates and sources
3. Mark the contradiction in frontmatter: `contradictions: [page-name]`
4. Flag for user review in the lint report

## Visual Aids
- Processes/workflows → ASCII or mermaid diagrams
- Comparisons → tables
- Taxonomies/hierarchies → tree or nested list
- Relationships/dependencies → flow diagrams

## Log Rotation
When log.md exceeds 500 entries, rotate to `log-YYYY.md` and start fresh.