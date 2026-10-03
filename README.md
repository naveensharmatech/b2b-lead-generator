# B2B Leads Scraper

Automate the discovery of local and B2B businesses from web search results, then optionally visit each business website to collect publicly listed email addresses and social profile links. The Apify Actor accepts business search terms and a location, and writes structured records to an Apify dataset.

[![Apify Actor](https://img.shields.io/badge/Apify-Actor-orange?logo=apify)](https://apify.com/opility/b2b-leads-scraper)
[![Node.js](https://img.shields.io/badge/Node.js-20-green?logo=node.js)](https://nodejs.org/)
[![License: ISC](https://img.shields.io/badge/License-ISC-blue.svg)](https://opensource.org/licenses/ISC)

**Try the live Actor:** [opility/b2b-leads-scraper](https://apify.com/opility/b2b-leads-scraper)  
**Published price positioning:** $1.50 per 1,000 leads. Check the live Store page for current pricing and billing details.

## At a glance

- Search for businesses by keyword/category and geographic location.
- Collect business names, result snippets, websites, and phone numbers when present in search snippets.
- Optionally scan the business homepage for email addresses and links to LinkedIn, Facebook, X/Twitter, and Instagram.
- Save records to the default Apify dataset for download and downstream processing.

### Project-reported results

The project reports **1,500+ leads processed** and a **100% automation rate**. These are project-reported figures, not independently audited benchmarks published with run logs. “100% automation” describes the automated Actor workflow; it does not mean every record contains an email, every contact is verified, or every run returns the requested number of results. See [Performance](docs/PERFORMANCE.md) for scope and measurement guidance.

## Technology

Apify SDK · Crawlee `CheerioCrawler` · Node.js 20 · JavaScript (ES modules) · Cheerio · `got-scraping`

## Categories and audiences

Use custom search terms for categories such as **Home Care**, **Medical Clinics**, **Dental Practices**, **IT Services**, **Software Companies**, **Marketing Agencies**, and **Real Estate Brokers**. These are search phrases, not a fixed category catalog or a guarantee of coverage. See [supported categories](docs/CATEGORIES.md).

Designed for SaaS teams, lead-generation agencies, and data teams that need a repeatable starting point for business prospect research. Common use cases include territory discovery, agency prospecting, local-business research, and building a list for human review before outreach.

## Quick start

1. Open the [live Apify Actor](https://apify.com/opility/b2b-leads-scraper).
2. Provide search terms and a target location. Optionally set the lead limit and website extraction options.
3. Run the Actor and review the output dataset before using it.

Example input:

```json
{
  "searchTerms": ["Home Care Agencies", "Dental Practices", "IT Services"],
  "location": "Austin, TX",
  "maxResults": 100,
  "extractEmails": true,
  "proxyConfiguration": {
    "useApifyProxy": true
  }
}
```

More details: [Setup](docs/SETUP.md), [API reference](docs/API-REFERENCE.md), and [example files](examples/).

## Pricing and practical ROI

At the advertised rate of $1.50 per 1,000 leads, 10,000 leads would cost **$15 in Actor usage** before any applicable platform charges, taxes, or other services. This is a simple usage-cost illustration, not a savings guarantee; compare current Store pricing and assess the quality and relevance of returned records for your own workflow.

This tool is an alternative workflow for business discovery—not a like-for-like replacement for Apollo, ZoomInfo, or Lusha. It does not provide a licensed contact database, verified decision-maker identities, or guaranteed email deliverability.

## How it works

The Actor creates search queries for each term and location, crawls DuckDuckGo HTML search results, deduplicates result URLs, and writes records to the dataset. When `extractEmails` is enabled, it makes one request to each result's website homepage to collect email-like strings and supported social links. It does not currently crawl multiple pages per website or validate email ownership/deliverability. See [Architecture](docs/ARCHITECTURE.md).

## Local development

```bash
npm install
npm test
```

To run with Apify's local Actor tooling, install/use the Apify CLI and run `npx apify-cli run` from the repository root. Set up an Apify account/token and proxy access if your selected configuration requires them. Deployment and environment details are in [Setup](docs/SETUP.md).

## Project and contact

Built by **Naveen Sharma**, Data Extraction Specialist, with a focus on Apify Actors, web scraping, and ETL architecture.

The project is published under the **Opility** brand. For Actor usage, support, and current product information, use the [Apify Store listing](https://apify.com/opility/b2b-leads-scraper).

## Documentation

- [Architecture and crawling strategy](docs/ARCHITECTURE.md)
- [Local setup and Apify deployment](docs/SETUP.md)
- [Business categories](docs/CATEGORIES.md)
- [Input and output reference](docs/API-REFERENCE.md)
- [Performance and optimization](docs/PERFORMANCE.md)
- [Examples](examples/)
- [Category examples](assets/category-examples.md)
- [Performance data notes](assets/performance-data.md)
- [Comparison and positioning](assets/comparison.md)

