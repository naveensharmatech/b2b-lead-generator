# Setup and deployment

## Run on Apify

1. Open the [B2B Leads Scraper Actor](https://apify.com/opility/b2b-leads-scraper) in Apify Store and sign in.
2. Configure at least one search term and a location. Review the [input reference](API-REFERENCE.md).
3. Configure proxy access if needed, then start a run.
4. Review the dataset output and download JSON, CSV, Excel, XML, or HTML from the Apify Console as appropriate.

Apify-hosted runs use the Actor definition in `.actor/actor.json` and the Node.js 20 image in `Dockerfile`. Proxy availability and usage charges depend on the account and selected configuration.

## Local development

Prerequisites: Node.js 20 and npm.

```bash
git clone https://github.com/naveensharmatech/b2b-lead-generator.git
cd b2b-lead-generator
npm install
npm test
```

`npm test` runs `node --check src/main.js` to check JavaScript syntax. It does not execute a live scrape.

To execute the Actor locally, use Apify's CLI:

```bash
npx apify-cli run
```

Provide Actor input through the local Actor tooling. An example is in [`examples/input-configuration.json`](../examples/input-configuration.json). A valid Apify account/token and proxy configuration may be required; never commit credentials to this repository. Local execution makes real requests to third-party search and business websites.

## Deploy code changes

The included `Dockerfile` uses `apify/actor-node:20`, installs production dependencies, and starts the Actor with `npm start`. Deploy through the Apify platform's normal Actor build/version workflow. Confirm the input schema, dataset output, proxy setup, and applicable source-site terms before production use.

## Troubleshooting

- **No or few records:** Try narrower/alternative search phrases or another location. Search results are externally controlled; `maxResults` is an upper bound, not a guarantee.
- **No email/social values:** Keep `extractEmails` enabled, confirm the result URL is reachable, and note that extraction inspects only that requested page.
- **Local run cannot access proxy:** Check Apify account/token and proxy access. Test without a proxy only where permitted and appropriate.
- **Test command reports syntax error:** Check the reported file/line and run `npm test` again after correcting it.
