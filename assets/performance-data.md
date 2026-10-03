# Performance data and measurement notes

## Project-reported figures

| Metric | Reported value | Interpretation |
| --- | --- | --- |
| Leads processed | 1,500+ | Cumulative project-reported count; no run log or benchmark dataset is included here for independent verification. |
| Automation rate | 100% | Project-reported automation of the Actor workflow, not a guarantee of successful requests, record completeness, or contact verification. |
| Positioned Actor usage price | $1.50 / 1,000 leads | Pricing statement in project materials; confirm the current price and billing model on Apify Store. |

## Runtime behavior to account for

- `maxResults` is a requested maximum, not a guaranteed output count.
- Each search term produces three query variations, and the crawler request ceiling is three times `maxResults`.
- With `extractEmails: true`, the Actor may additionally request one result URL per lead, each with a 10-second request timeout.
- Search relevance, external-site availability, proxy behavior, and request latency affect actual runtime and completeness.

## How to publish a reproducible benchmark

Record the Apify run ID, date/time, input terms and location, requested maximum, returned item count, elapsed time, and record completeness counts. Preserve the anonymized or permissioned run evidence alongside any future benchmark claim. Measure contact verification and deliverability separately because the Actor does not perform those checks.
