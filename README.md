<h1 align="center">Ángel Muñiz Pedraza</h1>
<p align="center">
  <b>Technical SEO &amp; GEO</b> — I make sites readable by Google <i>and</i> by the engines that answer instead of listing.
</p>
<p align="center">
  <a href="https://www.linkedin.com/in/angel-muniz-seo">LinkedIn</a> ·
  <a href="mailto:angelhd029@gmail.com">angelhd029@gmail.com</a> ·
  Sevilla, Spain / remote
</p>

---

> Español: SEO técnico y GEO. Hago que las webs se lean bien por Google **y** por los modelos que responden en vez de listar. Herramientas abajo; escríbeme en cualquiera de los dos idiomas.

Ranking and being cited are two different games. Site-level audits tell you whether the AI crawlers can get in; nothing told me whether a given page gave them anything worth quoting once they were inside — so I wrote the tools.

Nine of them, all Python, MIT, deterministic (no LLM calls, no API keys where avoidable), with tests and CI in green. This is the loop I run on real client sites.

### The GEO loop

| Stage | Tool | What it answers |
|---|---|---|
| 1. Can the AI crawlers read me? | **[geo-check](https://github.com/angelmunizpedraza/geo-check)** | Which engines can actually *cite* you, engine by engine — separating citation bots (OAI-SearchBot, PerplexityBot, Claude-SearchBot) from training bots (GPTBot, Google-Extended). Validates `llms.txt`, structured data and no-JS readability. |
| 2. Is anything there when they arrive? | **[render-gap](https://github.com/angelmunizpedraza/render-gap)** | Compares the HTML your server returns with the DOM after JavaScript, and reports exactly which headings, paragraphs, links and JSON-LD only exist in a browser. Those crawlers do not run JS, so anything client-side is invisible to them. Scored 0-100 and CI-gateable. |
| 3. Give them a map | **[llms-txt-generator](https://github.com/angelmunizpedraza/llms-txt-generator)** | Generates and validates `llms.txt` from the sitemap and the real content. |
| 4. Is this page quotable? | **[citeable](https://github.com/angelmunizpedraza/citeable)** | Scores one page 0-100 on 10 citability signals and returns an ordered list of which paragraph to rewrite. CI-gateable. |
| 5. Where do I rank but never get cited? | **[serp-to-ai-diff](https://github.com/angelmunizpedraza/serp-to-ai-diff)** | Compares Google's top 10 with what ChatGPT and Perplexity actually cite, per keyword. That gap is the GEO backlog. |
| 6. Am I being cited at all? | **[ai-visibility-tracker](https://github.com/angelmunizpedraza/ai-visibility-tracker)** | Brand mentions and citations inside AI answers, share of voice vs competitors, SQLite history, plus server-log analysis of real bot hits. |
| 7. Is my internal authority reaching the right pages? | **[linkjuice](https://github.com/angelmunizpedraza/linkjuice)** | Builds the internal link graph, finds orphans, click depth and internal PageRank, and returns concrete "link from *this* page to *that* page" recommendations. Counts body links only — nav and footer links are not votes. |
| 8. Is the classic SEO sound? | **[seo-audit](https://github.com/angelmunizpedraza/seo-audit)** | Crawls a site and returns indexing, content, performance and structured-data issues ranked by severity. |
| 9. Did it move traffic? | **[ga4-report](https://github.com/angelmunizpedraza/ga4-report)** | Organic traffic from the GA4 API with period-over-period comparison and landing-page alerts. Markdown, CSV or n8n webhook. |

### What I do with them

- **4,000 → 28,000 organic visits/month (7×)** and domain authority 12 → 27 on a group of online-education sites.
- **+119 % organic traffic in 2 months** and 10 keywords in the top 3 for a veterinary hospital in Los Angeles — English-language project, built end to end (React 19, Supabase, Cloudflare Workers).
- **~400 leads/month** handled with no spreadsheets: n8n + Apps Script + CRM + WhatsApp Business API, first contact under 2 minutes.

### Stack

`Python` · `pytest` · `GitHub Actions` · `BeautifulSoup` · `SQLite` · `GA4 Data API` · `Search Console` · `WordPress / WooCommerce` · `React` · `Google Ads` · `Meta Ads` · `GTM` · `n8n` · `SQL`

### Open to

Technical SEO / GEO roles, remote or on-site in Seville. Also happy to receive issues and PRs on any of the tools above — feedback from a comment on LinkedIn is what produced geo-check v0.2, and that is the best kind.
