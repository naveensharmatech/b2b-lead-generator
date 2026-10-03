# Architecture

## System overview

The Actor is a Node.js 20 JavaScript application built with the Apify SDK, Crawlee's `CheerioCrawler`, Cheerio, and `got-scraping`.

```text
Actor input
   │
   ├── searchTerms × location → DuckDuckGo HTML search pages
   │                                  │
   │                                  └── parse result title, snippet, URL
   │
   ├── optional homepage request → extract email-like strings and social links
   │
   └── deduplicate result URLs → write lead records to Apify Dataset
```

## Crawling strategy

1. Read Actor input and apply defaults for omitted values.
2. For each search term, create three query variations: `term in location`, `term companies in location`, and `term directory in location`.
3. Generate search page URLs for those variations. The number of pages is derived from `maxResults` and the number of terms, with at least two pages per variation.
4. Use Crawlee's `CheerioCrawler` to fetch and parse DuckDuckGo HTML result pages. The Actor caps crawler requests at three times `maxResults`.
5. Deduplicate leads by result website URL, then extract the title, search snippet, URL, category, and requested location. A phone number is taken from the snippet if a pattern matches.
6. If `extractEmails` is enabled and the result URL begins with `http`, make one request to that website URL. Parse email-like strings and links to LinkedIn, Facebook, X/Twitter, and Instagram from the returned page.
7. Push each record to the default Apify dataset until the requested `maxResults` count is reached or the available results are exhausted.

The current implementation does not use Google Maps, LinkedIn, or a dedicated business directory API as a search source. It does not crawl multiple pages of each business site, verify phone numbers, or confirm email ownership/deliverability. See [API Reference](API-REFERENCE.md) for output semantics.

## Reliability and limitations

- Crawling and source-search result availability depend on third-party websites and can vary by location, query, and time.
- A search result can have an empty or non-canonical URL; de-duplication is URL-based.
- The website request has a 10-second timeout. Failed website requests yield no emails and no social links for that page.
- Proxy behavior follows the supplied Apify proxy configuration and Actor runtime.
- Results are suitable for research and human review; do not treat extracted details as verified contact data.
