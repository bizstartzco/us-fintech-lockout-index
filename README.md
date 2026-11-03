# US Fintech Lockout Index

Which countries' residents are shut out of four US business-banking and payment providers, according to each provider's own published rules. 197 countries, scored 0 to 4. CSV and JSON, CC BY 4.0, no signup.

- Interactive version and full method: https://bizstartz.com/us-fintech-lockout-index/
- Data: [`data/us-fintech-lockout-index.csv`](data/us-fintech-lockout-index.csv) · [`data/us-fintech-lockout-index.json`](data/us-fintech-lockout-index.json)
- Version 1.0, published 16 October 2026

## Why this exists

Founders outside the US who form a US LLC usually ask the same first question: "can I open Mercury, Relay or Stripe from my country?" Each provider answers it on a different help page, in a different format, and the lists change without notice. This index puts the four published rule sets in one table so the answer for any country can be read in one row.

## Scoring

Each provider adds one point when its published rules shut out residents of a country. A country blocked by all four scores 4.

| Column | Meaning | Values |
|---|---|---|
| `rank` | Rank by score, ties share a rank | integer |
| `country` | Country or territory | text |
| `lockout_score` | Sum of the four provider columns | 0 to 4, in steps of 0.5 |
| `mercury_blocked` | 1 if the country is on Mercury's list of prohibited or sanctioned countries. Mercury applies this by where the owner lives, not citizenship. | 0 / 1 |
| `relay_blocked` | 1 if the country is on Relay's prohibited countries list. Relay applies this to any owner who holds citizenship or residency there. | 0 / 1 |
| `wise_usd_details_blocked` | 1 if any of: Wise says people with an address there cannot get USD account details; Wise Business restricts personal profiles with an address there; Wise does not operate there. | 0 / 1 |
| `stripe_local_status` | Whether a business registered in the country can sign up for Stripe locally. Scored: `Not listed` = 1, `Preview` or `Extended network` = 0.5, `Supported` = 0. | text |

## Sources

| Provider | Page |
|---|---|
| Mercury | https://support.mercury.com/hc/en-us/articles/28771710754580-Prohibited-countries |
| Relay | https://relayfi.com/hc/en-us/articles/10239600121748-Prohibited-Countries/ |
| Wise | https://wise.com/help/articles/2810318/can-i-get-usd-account-details , https://wise.com/help/articles/2978049/where-can-i-use-wise |
| Stripe | https://stripe.com/global |

All four pages were read on 16 October 2026. Mercury and Relay were re-checked against this file on 3 November 2026 with no changes: Mercury lists 48 prohibited countries plus sanctioned countries (Cuba, Iran, North Korea are scored as blocked), Relay lists 31.

## Limitations

- **Published rules only.** Every provider still reviews each application. A score of 0 means "not excluded on paper", not "you will be approved". Individual rejections do not show up here.
- **Rules change without notice.** Check the provider page before relying on a cell. The date each page was read is above.
- **Relay** also asks for a Social Security Number for each beneficial owner in its account-opening guide, so it can be harder in practice than its column shows.
- **Wise** needs a real physical trading address even where nothing is blocked; registered-agent, virtual-office and mail-forwarding addresses are not accepted. Wise's separate list of countries whose residents can hold money is not scored.
- **Stripe's column is about where the business is registered**, not where the owner lives. A US LLC applies under US rules, and Stripe still reviews the people behind it.
- **PayPal and Payoneer are not included.** Neither publishes a single country-by-country list.
- Mercury's list includes some EU members (Croatia, Latvia). That is what the page says on the date read; it is reproduced as published.

## Corrections

Found a wrong cell? Open an issue with the country, the column and a link to the provider page that shows it. Corrections are logged in [CHANGELOG.md](CHANGELOG.md) and credited. You can also email rahul@bizstartz.com.

## Licence and citation

Data: [CC BY 4.0](LICENSE). You may reuse and republish it, including commercially, as long as you credit Bizstartz and link to the source page.

> Bizstartz, "US Fintech Lockout Index", version 1.0, October 2026, https://bizstartz.com/us-fintech-lockout-index/

A [`CITATION.cff`](CITATION.cff) file is included, so GitHub's "Cite this repository" button gives the same reference.

Compiled by Rahul Shrestha, Co-Founder, Bizstartz. Bizstartz forms US LLCs for founders outside the US, so it has a commercial interest in this topic; the data is reproduced from the providers' own pages and is not adjusted in anyone's favour.
