# georeality-data

Two small data files that [geo-reality.com](https://geo-reality.com) reads while it renders
pages, so a daily data update needs no site deploy. A scheduled job in the (private) site
repository writes them once a day and commits only when something real changed.

| File | What it holds | Source |
|---|---|---|
| `situations.json` | Active natural-hazard alerts per country (ISO 3166-1 alpha-2): Orange and Red alerts only, events naming six or fewer countries, windows closed no more than seven days ago | [GDACS](https://www.gdacs.org/), the UN and European Commission's Global Disaster Alert and Coordination System |
| `travel-advisories.json` | UK Foreign, Commonwealth & Development Office advice against travel, per country: to the whole country or to parts of it, and at which level | [GOV.UK foreign travel advice](https://www.gov.uk/foreign-travel-advice), contains public sector information licensed under the [Open Government Licence v3.0](https://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/) |

Each file carries the time it was read (`generatedAt`, `readAt`). The site stops showing
alerts older than seven days and advice older than thirty, so a stopped job fails closed.

This is a convenience copy, not an authority: for travel decisions read the FCDO's own page
for the country, and GDACS for the event.
