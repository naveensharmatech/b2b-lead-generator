# Performance and optimization

## Reported figures

The project reports **1,500+ leads processed** and **100% automation**. These are project-reported figures. This repository does not include timestamped Actor run logs or a reproducible benchmark dataset with which to independently verify throughput, contact coverage, or completion rate.

The 100% figure refers to the automated Actor workflow and should not be interpreted as 100% successful records, complete contact details, verified data, or successful runs across all websites. `maxResults` is a ceiling; the Actor may return fewer records when searches yield fewer usable results or requests fail.

The Actor is positioned at **$1.50 per 1,000 leads** in project materials. Marketplace pricing can change; use the live [Apify Store listing](https://apify.com/opility/b2b-leads-scraper) for current pricing and billing terms.

## Operational factors

Run time and result volume depend on:

- Number and length of search terms, location specificity, and `maxResults`.
- Search-provider response times, result availability, and rate limiting.
- Whether optional website extraction is enabled; the current implementation may request one homepage per unique result.
- Website response times, 10-second per-request timeout, proxy behavior, and transient failures.

The implementation derives search pages from the desired maximum, uses three query variations per term, and sets `maxRequestsPerCrawl` to `maxResults × 3`. These are configuration bounds, not a throughput guarantee.

## Optimization guidance

- Start with a small `maxResults` and a few precise terms to inspect result relevance.
- Use focused searches and run separate locations to make quality easier to evaluate.
- Disable `extractEmails` when only business discovery is needed; this avoids additional homepage requests.
- Increase run size gradually, monitor completion and data quality, and use proxy settings according to your Apify account and source-site terms.
- Normalize, deduplicate, and manually validate records in your downstream system before outreach.

## Benchmarking responsibly

For a reproducible benchmark, retain the Actor run ID, input, run start/end times, dataset item count, and counts of records containing websites, phone-like strings, and email-like strings. Record the measurement window and query/location mix. Report completeness and verified deliverability separately; the Actor itself does not validate phone numbers or email deliverability.
