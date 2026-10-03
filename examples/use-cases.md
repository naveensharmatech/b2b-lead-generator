# Use cases

These workflows describe appropriate starting points for the Actor. Treat results as research leads that require review, not verified or consented contacts.

## Territory discovery

Set `searchTerms` to a small group of business types and `location` to one territory. Review the dataset for relevant companies, then export it for manual qualification.

## Agency prospecting

Search for a specific service provider type (for example, dental practices or managed IT providers) in a defined service area. A sales or agency team can triage results and enrich qualified companies using its own approved process.

## Data pipeline seed

Run the Actor on a schedule through Apify, consume dataset items through the Apify API, and pass them into a downstream CRM or warehouse after deduplication and validation. Implement appropriate consent, retention, and suppression controls in that downstream workflow.

## Cost illustration

At the project-positioned usage rate of $1.50 per 1,000 leads, a run returning 2,000 leads would imply $3 in Actor usage at that rate. Actual charges and current prices must be checked on the [Apify Store listing](https://apify.com/opility/b2b-leads-scraper); this illustration excludes all other expenses and does not imply a labor-savings or conversion guarantee.
