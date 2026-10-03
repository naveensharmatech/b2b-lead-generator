# Business categories

`searchTerms` accepts an array of free-form strings. The Actor combines every term with the supplied `location` to construct web search queries; there is no hard-coded category taxonomy or special category-specific extraction logic.

## Example search terms

| Area | Example terms |
| --- | --- |
| Home care | `Home Care Agencies`, `Home Health Providers`, `Senior Care Services` |
| Medical | `Medical Clinics`, `Urgent Care Clinics`, `Physical Therapy Clinics` |
| Dental | `Dental Practices`, `Pediatric Dentists`, `Orthodontists` |
| IT and software | `IT Services`, `Software Companies`, `Managed Service Providers` |
| Business services | `Marketing Agencies`, `Accounting Firms`, `Staffing Agencies` |
| Property | `Real Estate Brokers`, `Property Management Companies` |

These are query examples, not a promise that matching businesses or complete records will be found. Use the language that local businesses use in the target market and review sample results before scaling a run.

## Tips for useful queries

- Prefer concrete phrases such as `Dental Practices` over a very broad term like `Healthcare`.
- Use a specific city/region in `location` and run separate searches for distinct territories.
- Avoid adding too many overlapping phrases unless you need the breadth; overlapping search results are deduplicated by result URL.
- Check the resulting business category and location fields, which reflect the input query and location and are not independently classified or geocoded.
