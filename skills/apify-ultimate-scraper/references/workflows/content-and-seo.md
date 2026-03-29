# Content and SEO workflows

## Website content extraction for RAG
**When:** User wants to crawl a website and extract clean text for AI/LLM pipelines or knowledge bases.

### Pipeline
1. **Crawl website** -> `apify/website-content-crawler`
   - Key input: `startUrls`, `maxCrawlPages`, `crawlerType` ("cheerio" for speed, "playwright" for JS sites)

### Output fields
Step 1: `url`, `title`, `text`, `markdown`, `metadata`, `links[]`

### Gotcha
For JS-heavy sites (SPAs), set `crawlerType: "playwright"`. For static sites, use `"cheerio"` (10x faster). For anti-bot sites, use `apify/camoufox-scraper` instead.

## SERP analysis
**When:** User wants to analyze search engine results for specific keywords.

### Pipeline
1. **Google SERP** -> `apify/google-search-scraper`
   - Key input: `queries`, `maxPagesPerQuery`, `countryCode`, `languageCode`

### Output fields
Step 1: `organicResults[]` (title, url, description, position), `paidResults[]`, `peopleAlsoAsk[]`, `relatedSearches[]`

## Domain authority and backlink analysis
**When:** User wants SEO metrics for specific domains.

### Pipeline
1. **Traffic overview** -> `radeance/similarweb-scraper`
   - Key input: `urls`
2. **Backlink profile** -> `radeance/ahrefs-scraper`
   - Key input: `urls`
3. **Domain authority** -> `radeance/semrush-scraper`
   - Key input: `urls`

### Output fields
Step 1: `globalRank`, `monthlyVisits`, `bounceRate`, `trafficSources`
Step 2: `domainRating`, `backlinks`, `referringDomains`, `organicKeywords`
Step 3: `authorityScore`, `organicSearchTraffic`, `paidSearchTraffic`

### Gotcha
All radeance/ SEO Actors are PPE at $0.005-0.0275/result. Running all 3 for one domain costs ~$0.05-0.08. For 50 domains, estimate $2.50-$4.00.
