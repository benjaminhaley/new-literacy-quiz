# New Literacies Parent Quiz — Build Log

## What we built
A quick interactive quiz for parents based on the [New Literacies](https://newliteracies.ai/explore) framework — 8 research-backed capacities kids need to thrive in the AI age.

**Live quiz:** https://benjaminhaley.github.io/new-literacy-quiz/
**Code:** https://github.com/benjaminhaley/new-literacy-quiz

## How it works
1. Parent selects their child's age band (3–7, 8–12, 13+)
2. 8 questions — one per capacity (Agency, Persistence, Adaptability, Curiosity, Creativity, Judgment, Connection, Purpose)
3. Each question shows a research-backed tip for that age band, then 4 multiple-choice options
4. Results page shows scores sorted green → orange → red with links to learn more
5. Email capture CTA at the end

## How it was built (with Claude Code)
- **Scraped the real data** — the newliteracies.ai site is Astro/JS-rendered, so we pulled content from the JS bundle (`KnowledgeGraph.CzUws13B.js`) to get all 8 categories' "Try This" activities by age band
- **Single HTML file** — no build step, no dependencies, just one `index.html`
- **Styled to match** the original site's dark theme with emerald accents
- **Deployed via GitHub Pages** with a simple workflow

## Iteration
- v1: Basic quiz with dropdown age select, category labels, bars for scores
- v2 (current): Age band buttons, natural question phrasing, removed category labels from questions, colored dots instead of bars, sorted results, dark theme matching the original site, email CTA

Total time: ~30 minutes with Claude Code.
