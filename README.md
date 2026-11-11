<h1 align="center">Ángel Muñiz Pedraza</h1>
<p align="center">
  <b>Technical SEO &amp; GEO · Python automation</b> — I make sites readable by Google <i>and</i> by the engines that answer instead of listing, and I automate everything around them.
</p>
<p align="center">
  <a href="https://www.linkedin.com/in/angel-muniz-seo">LinkedIn</a> ·
  <a href="mailto:angelhd028@gmail.com">angelhd028@gmail.com</a> ·
  Sevilla, Spain / remote
</p>

---

> Español: SEO técnico, GEO y automatización con Python. Hago que las webs se lean bien por Google **y** por los modelos que responden en vez de listar, y automatizo lo que hay alrededor: captación, leads e informes. Herramientas abajo; escríbeme en cualquiera de los dos idiomas.

Ranking and being cited are two different games. Site-level audits tell you whether the AI crawlers can get in; nothing told me whether a given page gave them anything worth quoting once they were inside — so I wrote the tools.

Ten of them, all Python, MIT, with tests and CI in green. Nine are deterministic (no LLM calls, no API keys where avoidable); the tenth, **answerable**, does call a model, and then checks in plain code that every answer is backed by a quotation that really is on the page. This is the loop I run on real client sites.

All ten install with `pip`. Three of them — geo-check, seo-audit and render-gap — also ship as **GitHub Actions**, so a team can fail its own build the day a deploy blocks a citation bot or hides the copy behind JavaScript:

```yaml
- uses: angelmunizpedraza/geo-check@v1
  with: { url: https://example.com, fail-if-blocked: "true" }
```

### The GEO loop

| Stage | Tool | What it answers |
|---|---|---|
| 1. Can the AI crawlers read me? | **[geo-check](https://github.com/angelmunizpedraza/geo-check)** | Which engines can actually *cite* you, engine by engine — separating citation bots (OAI-SearchBot, PerplexityBot, Claude-SearchBot) from training bots (GPTBot, Google-Extended). Validates `llms.txt`, structured data and no-JS readability. |
| 2. Is anything there when they arrive? | **[render-gap](https://github.com/angelmunizpedraza/render-gap)** | Compares the HTML your server returns with the DOM after JavaScript, and reports exactly which headings, paragraphs, links and JSON-LD only exist in a browser. Those crawlers do not run JS, so anything client-side is invisible to them. Scored 0-100 and CI-gateable. |
| 3. Give them a map | **[llms-txt-generator](https://github.com/angelmunizpedraza/llms-txt-generator)** | Generates and validates `llms.txt` from the sitemap and the real content. |
| 4. Is this page quotable? | **[citeable](https://github.com/angelmunizpedraza/citeable)** | Scores one page 0-100 on 10 citability signals and returns an ordered list of which paragraph to rewrite. CI-gateable. |
| 5. Does it answer what buyers ask? | **[answerable](https://github.com/angelmunizpedraza/answerable)** | Sends the page and the real pre-purchase questions to a model, forces a structured verdict, and throws away any answer whose quotation is not on the page or that states a figure the quotation does not contain. Spend cap included; fails the build when the page cannot answer. |
| 6. Where do I rank but never get cited? | **[serp-to-ai-diff](https://github.com/angelmunizpedraza/serp-to-ai-diff)** | Compares Google's top 10 with what ChatGPT and Perplexity actually cite, per keyword. That gap is the GEO backlog. |
| 7. Am I being cited at all? | **[ai-visibility-tracker](https://github.com/angelmunizpedraza/ai-visibility-tracker)** | Brand mentions and citations inside AI answers, share of voice vs competitors, SQLite history, plus server-log analysis of real bot hits. |
| 8. Is my internal authority reaching the right pages? | **[linkjuice](https://github.com/angelmunizpedraza/linkjuice)** | Builds the internal link graph, finds orphans, click depth and internal PageRank, and returns concrete "link from *this* page to *that* page" recommendations. Counts body links only — nav and footer links are not votes. |
| 9. Is the classic SEO sound? | **[seo-audit](https://github.com/angelmunizpedraza/seo-audit)** | Crawls a site and returns indexing, content, performance and structured-data issues ranked by severity. |
| 10. Did it move traffic? | **[ga4-report](https://github.com/angelmunizpedraza/ga4-report)** | Organic traffic from the GA4 API with period-over-period comparison and landing-page alerts. Markdown, CSV or n8n webhook. |

### What I do with them

- **4,000 → 28,000 organic visits/month (7×)** and domain authority 12 → 27 on a group of online-education sites.
- **+119 % organic traffic in 2 months** and 10 keywords in the top 3 for a veterinary hospital microsite in Los Angeles — English-language project, built end to end (React 19, Supabase, Cloudflare Workers).
- **Relaunched the hospital's main site** in November 2026 on TanStack Start: LCP 5.8 s → 3.5 s, page weight 1.6 MB → 384 KB, CLS 0.128 → 0, 23 pages with zero axe accessibility errors.
- **~400 leads/month** handled with no manual work: Meta lead forms → Google Sheets → Conversions API → automatic WhatsApp (Apps Script + WhatsApp Business API).
- Launched **ChatGPT Ads** campaigns for two online-education brands (OpenAI Ads Manager, November 2026): bulk upload, bid and stop rules, and my own tracking on the WordPress side.

### Also built

- **[Lead_Scoring](https://github.com/angelmunizpedraza/Lead_Scoring)** — Master's thesis (KSchool): a calibrated CatBoost model that ranks which leads to call first using only pre-call data. ROC-AUC 0.767; calling the top 30 % captures 65 % of conversions.
- **[escaparate](https://github.com/angelmunizpedraza/escaparate)** — installable web app that reworks clothing photos with AI for second-hand marketplaces (Cloudflare Workers + GitHub Pages).
- Private, happy to walk through them in an interview: a client-prospecting platform (Python, Playwright, Google Places, AI agents under a spend cap), a computer-vision parking detector (D-FINE on ONNX Runtime, FastAPI) and a chess coach for Ray-Ban Meta glasses (Kotlin, FastAPI, OpenCV, Stockfish).

### Stack

`Python` · `pytest` · `GitHub Actions` · `Playwright` · `BeautifulSoup` · `SQLite` · `pandas` · `CatBoost` · `GA4 Data API` · `Search Console` · `TypeScript` · `React` · `TanStack Start` · `Cloudflare Workers` · `Supabase` · `WordPress / WooCommerce` · `Google Ads` · `Meta Ads` · `GTM` · `Apps Script` · `n8n` · `SQL`

### Open to

Technical SEO / GEO and Python automation roles, remote or on-site in Seville. Also happy to receive issues and PRs on any of the tools above — feedback from a comment on LinkedIn is what produced geo-check v0.2, and that is the best kind.
