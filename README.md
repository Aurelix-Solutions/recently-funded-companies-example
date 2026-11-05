# Recently Funded Companies: Python example

A small, runnable example for [Recently Funded Companies](https://apify.com/aurelix/recently-funded-companies), an Apify Actor by Aurelix.

## What it does

Recently Funded Companies turns the official SEC EDGAR Form D filings, the notices US companies file within 15 days of first selling shares, notes or SAFEs in a private round, into a clean lead list: company, state and city, industry group and sector, offering size, amount already sold, date of first sale, exemptions, revenue range, investor count, the executives, directors and promoters named on the form with their roles, and the filing link. Investment funds and SPVs are removed by default, so you get operating companies that just raised money. Turn on 'Only new filings since last run' and schedule it daily for a funding feed; optionally match each company's website and add its business emails, phones and decision-makers.

## Why this over alternatives

Compared with the leading alternatives on the Apify Store (the same table is on the Store page):

| | **This Actor** | pink_comic/sec-form-d-startup-funding-leads | logiover/sec-edgar-form-d-scraper |
|---|---|---|---|
| **Price per 1,000 filings, free plan** | $5 | $2 | $3.50 |
| **Price per 1,000 filings, paid plans** | $3.50 | $2 | $2 to $3 |
| **Start fee per run** | $0.006 | $0.0001 per GB | $0.00005 per GB |
| **Funds and SPVs removed by default** | ✓ | ✗ (industry filter only) | ✗ (industry filter only) |
| **Only new filings since last run** | ✓ free | ✗ | ✗ |
| **Company website, confirmed against the filing** | ✓ | ✗ | ✗ |
| **Website emails and decision-makers** | ✓ optional, charged only when found | ✗ | ✗ |
| **Executives and directors with roles** | ✓ name and role only | ✓ name and role | ✓ name, title and location |
| **Slack or webhook digest of new filings** | ✓ | ✗ (platform integrations only) | ✗ (platform integrations only) |
| **Source** | SEC Form D (official) | SEC Form D (official) | SEC Form D (official) |

- $5 per 1,000 filings ($3.50 on paid plans), against $70 to $80 for the most-used funding-lead Actors.
- Funds, SPVs and co-invest vehicles removed by default; other Form D Actors only filter by industry.
- Free 'only new since last run' mode for a daily feed with no repeats; other Form D Actors lack it.
- Company website confirmed against the filing, plus optional business emails and decision-makers, charged only when found.
- Executives, directors and promoters with their roles, never their addresses or locations.
- Straight from SEC EDGAR, public domain, linked to the filing; no login, no proxy.

## When to use it

- Sales teams selling to newly funded startups: software, recruiting, banking, insurance, office space
- Recruiters and staffing agencies reaching companies that just raised money and will hire
- VCs, angels and analysts tracking private rounds by sector and state
- Lenders, accountants and law firms finding companies at the moment they need advisers

## Input example

This is the `recently-funded-tech-startups` input used in `main.py`:

```json
{
  "daysBack": 7,
  "sectors": [
    "technology"
  ],
  "maxResults": 100
}
```

Every input field is documented on the [Store page](https://apify.com/aurelix/recently-funded-companies).

## How to run

1. Get an Apify API token from Apify Console (Settings, API & Integrations).
2. Install and run:

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
export APIFY_TOKEN=your_token_here
python main.py
```

The script starts a run of `aurelix/recently-funded-companies`, prints a few fields from the first results and writes every result to `results.csv`. Lists and nested objects are stored in the CSV as JSON text. Each run is billed to your Apify account (see Pricing below).

## Sample output

One record as returned by a real run (long text is shortened):

```json
{
  "accession_number": "0002162347-26-000001",
  "form_type": "D",
  "is_amendment": false,
  "previous_accession_number": null,
  "filing_date": "2026-11-04",
  "company_name": "Newcoda, Inc.",
  "cik": "0002162347",
  "entity_type": "Corporation",
  "jurisdiction_of_incorporation": "Florida",
  "year_of_incorporation": 2026,
  "incorporated_within_5_years": true,
  "street": "8600 NW 17th ST",
  "city": "Miami",
  "state": "FL",
  "state_name": "Florida",
  "zip_code": "33126",
  "phone": "3054778700",
  "industry_group": "Other Technology",
  "sector": "technology",
  "investment_fund_type": null,
  "is_pooled_fund": false,
  "revenue_range": "Decline to Disclose",
  "net_asset_value_range": null,
  "federal_exemptions": [
    "06b"
  ],
  "securities_offered": [
    "Other",
    "SAFE"
  ],
  "date_of_first_sale": "2026-10-01",
  "first_sale_yet_to_occur": false,
  "more_than_one_year": false,
  "total_offering_amount": 1800000,
  "offering_amount_indefinite": false,
  "total_amount_sold": 1265000,
  "total_remaining": 535000,
  "minimum_investment": 25000,
  "investors_count": 14,
  "has_non_accredited_investors": false,
  "sales_commissions": 0,
  "finders_fees": 0,
  "related_persons": [
    {
      "name": "Betina Kitzler",
      "roles": [
        "Executive Officer",
        "Director"
      ],
      "clarification": null
    },
    {
      "name": "Alberto Gross",
      "roles": [
        "Executive Officer",
        "Director"
      ],
      "clarification": null
    },
    {
      "name": "Jose Ignacio Cordero Ehrenberg",
      "roles": [
        "Executive Officer",
        "Director"
      ],
      "clarification": null
    },
    "... [1 more]"
  ],
  "signer_name": "Betina Kitzler",
  "signer_title": "CEO",
  "website": "https://newcoda.ai/",
  "contacts": {
    "emails": [
      {
        "email": "contact@newcoda.ai",
        "source_url": "https://newcoda.ai/"
      }
    ],
    "phones": [],
    "social_profiles": [
      {
        "network": "linkedin",
        "url": "https://www.linkedin.com/company/newcoda-ai",
        "source_url": "https://newcoda.ai/"
      }
    ],
    "people": [
      {
        "name": "Pilar Savoldi",
        "title": "Co-Founder",
        "seniority": "founder_owner",
        "function": "executive",
        "work_email": null,
        "work_phone": null,
        "source_url": "https://newcoda.ai/company/"
      },
      {
        "name": "Luis Luna",
        "title": "Co-Founder & Head of Engineering",
        "seniority": "founder_owner",
        "function": "engineering",
        "work_email": null,
        "work_phone": null,
        "source_url": "https://newcoda.ai/company/"
      }
    ]
  },
  "filing_url": "https://www.sec.gov/Archives/edgar/data/2162347/000216234726000001/0002162347-26-000001-index.htm",
  "xml_url": "https://www.sec.gov/Archives/edgar/data/2162347/000216234726000001/primary_doc.xml",
  "source_url": "https://www.sec.gov/Archives/edgar/data/2162347/000216234726000001/0002162347-26-000001-index.htm",
  "scraped_at": "2026-11-04T22:17:07Z"
}
```

## Export to CSV

`main.py` writes `results.csv` with the `csv` module. You can also download any run's results directly:

```
https://api.apify.com/v2/datasets/<datasetId>/items?format=csv&clean=true
```

Send your token in an `Authorization: Bearer <token>` header (or `?token=`) if the dataset is not readable without one. Other formats: `format=json`, `format=xlsx`.

## Google Sheets

- Simplest: use Apify's Google Sheets integration on the Actor or a saved task, so each run's results land in a sheet with no token in the sheet itself.
- Quick pull of one run: `=IMPORTDATA("https://api.apify.com/v2/datasets/<datasetId>/items?format=csv&clean=true")`. This only works without a token if your account lets anyone with the dataset ID read it. Do not paste an API token into a sheet formula: anyone who can view or copy the sheet can read it and use your account.

## n8n

- Apify node: choose "Run an Actor", enter `aurelix/recently-funded-companies`, paste the input above, then read the run's dataset items.
- HTTP Request node: `POST https://api.apify.com/v2/acts/aurelix~recently-funded-companies/run-sync-get-dataset-items` with header `Authorization: Bearer <token>` (stored as an n8n credential) and the input as the JSON body. The response is the list of results. This endpoint waits for the run to finish, so for large runs start the run asynchronously and fetch the dataset when it ends.

## Limits

- Form D covers only US private offerings under Regulation D and 4(a)(5): no investor names, no round name (seed, Series A), and companies that raise without filing are missing.
- Amounts are as filed; 'Indefinite' offering sizes come back as an empty total_offering_amount with offering_amount_indefinite true.
- The fund filter uses the filing's industry group, 3(c) exclusions and vehicle words in the name; a fund that files as an operating industry under a plain name is not caught, and an operating company named like a fund (e.g. 'Fund' or 'Aggregator' in its name) is dropped unless you switch the filter off.
- The issuer street is left empty when it equals a related person's address, which also happens when executives list the office as their address.
- Website match: only when the company name works as a .com, .ai, .io or .co domain and the site shows the issuer's city or phone; most small issuers get none.
- Website contacts come only from what the company publishes on its own site (up to 5 pages); sites that block crawlers in robots.txt are skipped.
- Days are EDGAR filing dates, counted back from today in UTC; 'Filed in the last N days' is capped at 90, and EDGAR search returns at most 10,000 filings per day (far above the real volume). EDGAR's daily form index lists filings by acceptance day, so it can differ by one or two: on one test day we returned 248 Form D and D/A filings, the index listed 247, and the extra one was dated that day but accepted the next.
- Pace: up to 5 SEC requests per second, about one per filing, so 1,000 filings take a few minutes; the SEC may slow runs that share an IP with heavy users.

## Pricing

At the time of writing:

Pay per event: you pay only for what the run returns, plus a small start fee.

| Event | Free plan | Paid plans (Bronze, Silver, Gold) |
|---|---|---|
| `filing-result` | $5.00 per 1,000 filings | $3.50 per 1,000 filings |
| `contact-result` | $15.00 per 1,000 companies with contacts | $15.00 per 1,000 companies with contacts |
| `apify-actor-start` | $0.006 per run | $0.006 per run |

Filings that do not match your filters, filings seen by an earlier run (with 'Only new filings since last run'), suppressed names and unreadable filings are not charged. A contact-result is charged only for a company whose website gave at least one email, phone, social link or named person.

Check the [Store page](https://apify.com/aurelix/recently-funded-companies) for current prices.

## Links

- Actor: https://apify.com/aurelix/recently-funded-companies
- Questions, bugs and feature requests: the Issues tab on the Store page.

## Licence

The example code in this repository is released under the MIT licence (see `LICENSE`). The Actor itself runs on Apify and is billed through your Apify account.
