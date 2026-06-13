[Dice Com Job Scraper](https://apify.com/blackfalcondata/dice-com-job-scraper?fpr=data)

## What does Dice.com Job Scraper do?

Dice.com Job Scraper extracts structured job data from [dice.com](https://dice.com) — including salary data, contact details, company metadata, full descriptions, location data, and skill tags. It supports keyword search, location filters, and controllable result limits, so you can run the same query consistently over time. The actor also offers detail enrichment (full descriptions, company profiles, and contact information) where the source provides them.

**New to Apify?** [Sign up free](https://console.apify.com/sign-up?fpr=1h3gvi) and use the included $5 monthly platform credit to test this actor.

## Key features

- **Incremental mode** — recurring runs emit and charge only for listings that are new or whose tracked content changed. First run builds the baseline state; subsequent runs emit only new or changed records.
- **Detail enrichment** — full descriptions, company profiles, and contact information where the source provides them.
- **Compact mode** — AI-agent and MCP-friendly payloads with core fields only.

## What data can you extract from dice.com?

Each result includes Core listing fields (`jobId`, `jobKey`, `title`, `location`, `postalCode`, `applicantLocationRequirements`, `salaryText`, and `salaryMin`, and more), detail fields when enrichment is enabled (`description`, `descriptionHtml`, `descriptionLength`, and `detailFetched`), contact and apply information (`easyApply`, `applyUrl`, `extractedEmails`, and `contactName`), and company metadata (`company`, `companyUrl`, `companyProfileId`, and `companyLogoUrl`). In standard mode, all fields are always present — unavailable data points are returned as `null`, never omitted. In compact mode, only core fields are returned.

Enable detail enrichment in the input to get richer fields such as full descriptions, company profiles, and contact information where the source provides them.

## Input

The main inputs are a search keyword, an optional location filter, and a result limit. Additional filters and options are available in the input schema.

Key parameters:

- **`query`** — Job search keywords. Use JSON array for multi-query, e.g. ["python", "java"].
- **`location`** — City, state, or region. Use JSON array for multi-location, e.g. ["New York", "San Francisco"].
- **`radius`** — Distance radius from location in miles. Common values: 10, 25, 50, 75, 100.
- **`employmentType`** — Filter by employment type.
- **`remoteFilter`** — Filter by workplace type.
- **`employerType`** — Filter by employer type.
- **`easyApply`** — Only return jobs that support Easy Apply. (default: `false`)
- **`postedDate`** — Only return jobs posted within this time period.
- **`startUrls`** — Direct Dice search or job detail URLs. Overrides query/location.
- **`maxResults`** — Maximum total job listings to return. 0 = unlimited. (default: `25`)
- **`maxPages`** — Maximum SERP pages to scrape per search source. (default: `5`)
- **`pageSize`** — Number of job listings per search page. Higher values mean fewer requests but larger responses. (default: `20`)
- ...and 9 more parameters

### Input examples

**Basic search** — Keyword-driven search scoped to a city with a tight radius.

→ Full payload per result — all standard fields populated where the source provides them.

```
{
  "query": "software engineer",
  "location": "New York",
  "maxResults": 50
}
```

**Incremental tracking** — Only emit jobs that changed since the previous run with this `stateKey`.

→ First run builds the baseline state. Subsequent runs emit only records that are new or whose tracked content changed. Set `emitUnchanged: true` to include unchanged records as well.

```
{
  "query": "software engineer",
  "maxResults": 200,
  "incrementalMode": true,
  "stateKey": "software-engineer-tracker"
}
```

**Compact filtered output** — Combine filters with compact mode for a lightweight AI-agent or MCP data source.

→ Core fields only — ideal for piping into LLMs or downstream tools without token overhead.

```
{
  "query": "software engineer",
  "employmentType": "Full-time",
  "maxResults": 50,
  "compact": true
}
```

## Output

Each run produces a dataset of structured job records. Results can be downloaded as JSON, CSV, or Excel from the Dataset tab in Apify Console.

### Example job record

```
{
  "jobId": "09be02b4589309e355b2d783a450d18ea8a09622ee6ca6ae1dcceda4180f2895",
  "jobKey": "5cf13c8d-bea1-4ff8-b734-99681e3b69eb",
  "title": "Sr Software Engineer",
  "company": "Randstad Digital",
  "companyUrl": null,
  "companyProfileId": "ee3855f3-d056-5325-bc31-ad5f53052a28",
  "companyLogoUrl": "https://d3qscgr6xsioh.cloudfront.net/nwd2B9CDT8Oo4K91VMeJ_transformed.png?format=webp",
  "location": "Jersey City, New Jersey, USA",
  "postalCode": "07310",
  "applicantLocationRequirements": "USA",
  "description": "job summary:Proficient in working with Oracle/CrDB, creating & leading database objects like tables, views, indexes, Stored Procs and optimizing database performance through query tuning, indexing, an...",
  "descriptionHtml": "job summary:<br><br><p>Proficient in working with Oracle/CrDB, creating &amp; leading database objects like tables, views, indexes, Stored Procs and optimizing database performance through query tunin...",
  "descriptionLength": 2030,
  "salaryText": "USD72 - USD73",
  "salaryMin": 72,
  "salaryMax": 73,
  "salaryCurrency": "USD",
  "salaryType": null,
  "employmentType": "CONTRACTOR",
  "workplaceTypes": [
    "On-Site"
  ],
  "employerType": "Recruiter",
  "skills": [],
  "easyApply": false,
  "postedDate": "2026-04-02T18:04:39.000Z",
  "modifiedDate": "2026-04-04T18:02:44Z",
  "validThrough": "2026-05-05T18:02:44.000Z",
  "canonicalUrl": "https://www.dice.com/job-detail/5cf13c8d-bea1-4ff8-b734-99681e3b69eb",
  "applyUrl": null,
  "portalUrl": "https://www.dice.com",
  "sourceUrl": "https://www.dice.com/job-detail/5cf13c8d-bea1-4ff8-b734-99681e3b69eb",
  "sourceCountry": "US",
  "sourceDomain": "www.dice.com",
  "searchQuery": "software engineer",
  "searchUrl": "https://www.dice.com/jobs?q=software+engineer&location=New+York&pageSize=20&language=en",
  "isSponsored": false,
  "fetchedAt": "2026-04-04T20:45:36.071Z",
  "scrapedAt": "2026-04-04T20:45:36.071Z",
  "detailFetched": true,
  "contentQuality": "full",
  "extractedEmails": [],
  "contactName": null,
  "diceJobId": null,
  "positionId": null,
  "companyIndustry": null,
  "companyEmployeeRange": null,
  "companyWebsite": null,
  "companyDescription": null
}
```

### Incremental fields

When `incremental: true`, each record also carries:

- `changeType` — one of `NEW`, `UPDATED`, `UNCHANGED`, `REAPPEARED`, `EXPIRED`. Default output covers `NEW` / `UPDATED` / `REAPPEARED`; set `emitUnchanged: true` or `emitExpired: true` to opt into the others.
- `firstSeenAt`, `lastSeenAt` — ISO-8601 timestamps tracking the listing across runs.
- `isRepost`, `repostOfId`, `repostDetectedAt` — populated when a new listing matches the tracked content of a previously expired one. Set `skipReposts: true` to drop detected reposts from the output.

## How to scrape dice.com

1. Go to [Dice.com Job Scraper](https://apify.com/blackfalcondata/dice-com-job-scraper?fpr=1h3gvi) in Apify Console.
2. Enter a search keyword and optional location filter.
3. Set `maxResults` to control how many results you need.
4. Enable `includeDetails` if you need full descriptions, contact info, or company data.
5. Click **Start** and wait for the run to finish.
6. Export the dataset as JSON, CSV, or Excel.

## Use cases

- Extract job data from dice.com for market research and competitive analysis.
- Track salary trends across regions and categories over time.
- Monitor new and changed listings on scheduled runs without processing the full dataset every time.
- Build outreach lists using contact details and apply URLs from listings.
- Research company hiring patterns, employer profiles, and industry distribution.
- Use structured location data for regional analysis, mapping, and geo-targeting.
- Feed structured data into AI agents, MCP tools, and automated pipelines using compact mode.
- Export clean, structured data to dashboards, spreadsheets, or data warehouses.
- Analyze skill demand across listings using structured skill tags.

## How much does it cost to scrape dice.com?

Dice.com Job Scraper uses [pay-per-event](https://apify.com/pricing?fpr=1h3gvi) pricing. You pay a small fee when the run starts and then for each result that is actually produced.

- **Run start:** $0.01 per run
- **Per result:** $0.002 per job record

Example costs:

- 10 results: **$0.03**
- 100 results: **$0.21**
- 500 results: **$1.01**

### Example: recurring monitoring savings

These examples compare full re-scrapes with incremental runs at different churn rates. Churn is the share of listings that are new or whose tracked content changed since the previous run. Actual churn depends on your query breadth, source activity, and polling frequency — the scenarios below are examples, not predictions.

Example setup: 100 results per run, daily polling (30 runs/month). Event-pricing examples scale linearly with result count.

| Churn rate | Full re-scrape run cost | Incremental run cost | Savings vs full re-scrape | Monthly cost after baseline |
| --- | --- | --- | --- | --- |
| 5% — stable niche query | $0.21 | $0.02 | $0.19 (90%) | $0.60 |
| 15% — moderate broad query | $0.21 | $0.04 | $0.17 (81%) | $1.20 |
| 30% — high-volume aggregator | $0.21 | $0.07 | $0.14 (67%) | $2.10 |

Full re-scrape monthly cost at daily polling: $6.30. First month with incremental costs $0.79 / $1.37 / $2.24 for the 5% / 15% / 30% scenarios because the first run builds baseline state at full cost before incremental savings apply.

 

## FAQ

### How many results can I get from dice.com?

The number of results depends on the search query and available listings on dice.com. Use the `maxResults` parameter to control how many results are returned per run.

### Does Dice.com Job Scraper support recurring monitoring?

Yes. Enable incremental mode to only receive new or changed listings on subsequent runs. This is ideal for scheduled monitoring where you want to track changes over time without re-processing the full dataset.

### Can I integrate Dice.com Job Scraper with other apps?

Yes. Dice.com Job Scraper works with Apify's [integrations](https://apify.com/integrations?fpr=1h3gvi) to connect with tools like Zapier, Make, Google Sheets, Slack, and more. You can also use webhooks to trigger actions when a run completes.

### Can I use Dice.com Job Scraper with the Apify API?

Yes. You can start runs, manage inputs, and retrieve results programmatically through the Apify API. Client libraries are available for JavaScript, Python, and other languages.

### Can I use Dice.com Job Scraper through an MCP Server?

Yes. Apify provides an [MCP Server](https://apify.com/apify/actors-mcp-server?fpr=1h3gvi) that lets AI assistants and agents call this actor directly. Use compact mode and `descriptionMaxLength` to keep payloads manageable for LLM context windows.

### Is it legal to scrape dice.com?

This actor extracts publicly available data from dice.com. Web scraping of public information is generally considered legal, but you should always review the target site's terms of service and ensure your use case complies with applicable laws and regulations, including GDPR where relevant.

### Your feedback

If you have questions, need a feature, or found a bug, please [open an issue](https://apify.com/blackfalcondata/dice-com-job-scraper/issues?fpr=1h3gvi) on the actor's page in Apify Console. Your feedback helps us improve.

## You might also like

- [Adzuna Job Scraper](https://apify.com/blackfalcondata/adzuna-scraper?fpr=1h3gvi) — Scrape adzuna.com - the global job board with 20+ country markets. Structured salary.
- [APEC.fr Scraper - French Executive Jobs](https://apify.com/blackfalcondata/apec-scraper?fpr=1h3gvi) — Scrape apec.fr - French executive job listings with salary ranges, company, location, skills,.
- [Arbeitsagentur Scraper - German Jobs](https://apify.com/blackfalcondata/arbeitsagentur-scraper?fpr=1h3gvi) — Scrape arbeitsagentur.de - Germany’s official employment portal with 1M+ listings. Contact data,.
- [AutoScout24 Scraper](https://apify.com/blackfalcondata/autoscout24-scraper?fpr=1h3gvi) — Scrape autoscout24.com - Europe's largest used car marketplace with 770K+ listings. Structured.
- [Bayt.com Scraper - Jobs from the Middle East](https://apify.com/blackfalcondata/bayt-scraper?fpr=1h3gvi) — Scrape bayt.com - the leading Middle East job board. Salary data, experience requirements.
- [Bilbasen Scraper - Denmark’s Car Marketplace](https://apify.com/blackfalcondata/bilbasen-scraper?fpr=1h3gvi) — Scrape bilbasen.dk - Denmark’s largest car marketplace. Full vehicle specifications, seller.
- [Bumeran Scraper](https://apify.com/blackfalcondata/bumeran-scraper?fpr=1h3gvi) — Scrape bumeran.com.ar - the largest job board across 8 LATAM countries. Work modality, contract.
- [Cadremploi Job Scraper](https://apify.com/blackfalcondata/cadremploi-scraper?fpr=1h3gvi) — Scrape cadremploi.fr - French management and executive jobs. Salary ranges, apply links.

## Getting started with Apify

New to Apify? [Create a free account with $5 credit](https://console.apify.com/sign-up?fpr=1h3gvi) — no credit card required.

1. Sign up — $5 platform credit included
2. Open this actor and configure your input
3. Click **Start** — export results as JSON, CSV, or Excel

Need more later? [See Apify pricing](https://apify.com/pricing?fpr=1h3gvi).