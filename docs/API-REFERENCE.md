# API reference

The Actor input is configured in [`.actor/input_schema.json`](../.actor/input_schema.json). Records are written to the default Apify dataset. Dataset exports can be downloaded from Apify Console in supported formats.

## Input

| Field | Type | Required by schema | Default | Description |
| --- | --- | --- | --- | --- |
| `searchTerms` | string array | Yes | `["Software Companies", "Marketing Agencies", "IT Services", "Real Estate Brokers", "Healthcare Clinics"]` in code | Search phrases; each phrase is queried with the requested location. |
| `location` | string | Yes | `"New York, NY"` in code | Target city, region, or country. |
| `maxResults` | integer | No | `100` | Maximum number of records to write. Schema allows 1–50,000; fewer may be returned. |
| `extractEmails` | boolean | No | `true` | When enabled, request each result website homepage for email-like strings and supported social links. |
| `proxyConfiguration` | object | No | Apify SDK default when omitted | Apify proxy configuration passed to the crawler and website requests. |

Note: `searchTerms` and `location` are marked required by the schema even though the source code has defaults. Provide both explicitly in API requests for consistent behavior.

## Output record

| Field | Type | Description |
| --- | --- | --- |
| `title` | string | Title parsed from the search result. |
| `category` | string | Search term used for the result. |
| `location` | string | Input location; not a verified street address. |
| `snippet` | string | Search result snippet, if provided. |
| `website` | string or null | Search result destination URL. |
| `phone` | string or null | First phone-like pattern found in the search snippet; not validated. |
| `email` | string or null | First extracted email-like string, or null if none was found. |
| `allEmails` | string array | Distinct email-like strings found in the snippet and, when enabled, requested homepage. |
| `socialLinks` | object | `linkedin`, `facebook`, `twitter`, and `instagram` URLs when found; values may be null or absent if no homepage extraction occurred. |
| `scrapedAt` | ISO date-time string | Time the record was created by the Actor. |
| `source` | string | Currently `"Opility B2B Engine"`. |

An extracted email is not necessarily verified. The Actor does not validate deliverability or contact identity.

## Example

See [`examples/input-configuration.json`](../examples/input-configuration.json) and [`examples/output-samples.json`](../examples/output-samples.json). The output example is illustrative and uses reserved example-domain values; it is not a live business lead.
