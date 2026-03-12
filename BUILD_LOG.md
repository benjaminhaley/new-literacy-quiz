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

---

## Full Prompt Transcript

### Prompt 1 — Initial request
> Consider this website: https://newliteracies.ai/explore/connection. I gave the following feedback: Quick gut reaction — I started caring when I saw the "try this" section. Might try to get users there even from homepage. Related, wonder if you could turn that into a quick quiz that lets you know as a parent how well you are supporting your kid on these core new literacies?
>
> Can you help me build that quiz? Can be very simple to start. First say your kids age. Then it should ask whether you have done the suggested activity by grade band. Based on your answer it should give you a score for the key categories and a link to the section to learn more. For the first pass just do the 8 major categories not all of the sub categories. Make answers multiple choice and try to give reasonable options. Don't worry about look and feel much on the first pass. Ideally we could put this somewhere basic hosted to make it easy to share, but don't worry about making it a nice looking url.
>
> *(attached screenshot of the Connection page with "Try This" section highlighted)*

**What Claude did:** Tried to fetch newliteracies.ai but the site is heavily JS-rendered (Astro framework), so standard web fetching only returned navigation chrome. No "Try This" content was visible in the HTML.

### Prompt 2 — Nudge to crawl JS content
> Can't you find a way to crawl and read it even if it's JS rendered?

**What Claude did:** Downloaded the raw HTML (98KB), found it was an Astro site, discovered the content was embedded in a JS bundle (`KnowledgeGraph.CzUws13B.js` — 351KB). Searched the bundle for "Ages 3" and found all the "Try This" activities. Extracted the full tryThis data for all 8 categories with a Python script. Built v1 of the quiz as a single `index.html`.

### Prompt 3 — Visual feedback with annotated screenshots
> Thanks! Quick feedback in screenshots. Can you address this? Also:
> 1. Can you match the general style of the original site
> 2. At the end as a call to action ask them to input their email if they want to receive regular new literacy tips
>
> *(attached 3 annotated screenshots showing:)*
> - *Age select: "Make multiple choice, match ranges on site (3-7, 8-12, 13+)"*
> - *Questions: "Make these more legible. Remove the category labels. Don't worry about directly quoting. Phrase in a natural readable way"*
> - *Results: "Update order, put green at top, then orange then red" and "Make red, orange and green all dots like red — dots not bars"*

**What Claude did:** Fetched the site's CSS to extract the color palette (dark background, stone tones, emerald accents). Rewrote the entire quiz: age band buttons instead of dropdown, natural question phrasing without category labels, research tips without the "Try This (Ages X):" prefix, dark theme matching the original site, colored dots sorted by score, email CTA at the end.

### Prompt 4 — Deploy it
> Looks great, can you please give it a public url. Maybe GitHub makes that easy?

**What Claude did:** Created a new public GitHub repo (`new-literacy-quiz`), pushed the code, set up GitHub Pages with a deploy workflow. Live in under 2 minutes.

### Prompt 5 — Share the work
> Can you help me generate a quick way to share the code and this chat?

**What Claude did:** Created this build log and pushed it to the repo.

### Prompt 6 — Share the prompts
> Can I actually share the prompts? Perfect, transcript is great — please add to the bottom of the build log doc.

**What Claude did:** Added this transcript.
