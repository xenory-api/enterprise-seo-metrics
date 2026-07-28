# Ahrefs Metric Definitions

Comprehensive reference documentation for all SEO metrics returned by the **Ahrefs Metrics** endpoint.

These metrics are sourced from Ahrefs' SEO index and provide insights into domain authority, backlink profiles, organic search visibility, keyword performance, and paid search activity.

# Table of Contents

- [Overview](#overview)
- [Authority Metrics](#authority-metrics)
  - [Domain Rating](#domain-rating-domain_rating)
  - [URL Rating](#url-rating-url_rating)
  - [Ahrefs Rank](#ahrefs-rank-ahrefs_rank)
  - [Domain Rank](#domain-rank-domain_rank)
- [Backlink Metrics](#backlink-metrics)
  - [Backlinks](#backlinks-backlinks)
  - [Referring Domains](#referring-domains-referring_domains)
  - [Live Backlinks](#live-backlinks-live_backlinks)
  - [All-Time Backlinks](#all-time-backlinks-all_time_backlinks)
  - [Live Referring Domains](#live-referring-domains-live_referring_domains)
  - [All-Time Referring Domains](#all-time-referring-domains-all_time_referring_domains)
- [Organic Search Metrics](#organic-search-metrics)
  - [Organic Traffic](#organic-traffic-organic_traffic)
  - [Organic Cost](#organic-cost-organic_cost)
  - [Organic Keywords](#organic-keywords-organic_keywords)
  - [Organic Keywords Positions 1–3](#organic-keywords-positions-1-3-organic_keywords_1_3)
- [Paid Search Metrics](#paid-search-metrics)
  - [Paid Traffic](#paid-traffic-paid_traffic)
  - [Paid Cost](#paid-cost-paid_cost)
  - [Paid Pages](#paid-pages-paid_pages)
  - [Paid Keywords](#paid-keywords-paid_keywords)
- [Usage Notes](#usage-notes)

# Overview

The **Ahrefs Metrics** endpoint provides SEO intelligence across domains, exact URLs, and subdomains.

Metrics are divided into three primary datasets:

- Domain metrics
- Exact URL metrics
- Subdomain metrics

These metrics are commonly used for:

- Backlink analysis
- Domain authority evaluation
- Competitor research
- Organic search monitoring
- Keyword research
- PPC analysis
- SEO reporting

Ahrefs metrics are estimates generated from Ahrefs' proprietary index and should be interpreted as comparative indicators rather than absolute measurements.

# Authority Metrics

## Domain Rating (`domain_rating`)

### Description

Domain Rating (DR) is Ahrefs' proprietary metric that estimates the overall strength of a website's backlink profile.

The score is primarily based on the quantity and quality of external websites linking to a domain.

### Data Type

`integer`

### Range

$0–100$

### Example

```json
{
  "domain_rating": 99
}
```

### Interpretation

Generally:

- Higher values indicate stronger backlink authority.
- Lower values indicate weaker or less established backlink profiles.

Because the scale is logarithmic, increasing from a high DR score requires significantly more authoritative backlinks than increasing from a lower score.

### Common Uses

- Domain comparison
- Competitor analysis
- Link prospect evaluation
- SEO reporting

### Notes

Domain Rating is a third-party SEO metric and is not a Google ranking factor.

## URL Rating (`url_rating`)

### Description

URL Rating (UR) estimates the strength of an individual URL's backlink profile.

Unlike Domain Rating, URL Rating focuses on links pointing to a specific page rather than the entire domain.

### Data Type

`integer`

### Range

$0–100$

### Example

```json
{
  "url_rating": 68
}
```

### Interpretation

Higher values generally indicate stronger page-level backlink authority.

### Common Uses

- Page authority evaluation
- Link building analysis
- Content performance comparison

## Ahrefs Rank (`ahrefs_rank`)

### Description

Ahrefs Rank is a global ranking system that orders websites based on the strength and size of their backlink profiles.

### Data Type

`integer`

### Example

```json
{
  "ahrefs_rank": 3
}
```

### Interpretation

Lower values represent stronger rankings.

For example:

- Rank $1$ represents the strongest domains in the Ahrefs index.
- Higher rank numbers indicate relatively weaker backlink profiles.

### Common Uses

- Global domain comparison
- Competitive research

## Domain Rank (`domain_rank`)

### Description

Domain Rank represents the relative position of a domain within Ahrefs' ranking system.

### Data Type

`integer`

### Example

```json
{
  "domain_rank": 3
}
```

### Interpretation

Lower values generally indicate stronger domain-level authority.

# Backlink Metrics

## Backlinks (`backlinks`)

### Description

The total number of backlinks discovered pointing to a domain or URL.

A backlink represents an external hyperlink from another website.

### Data Type

`integer`

### Example

```json
{
  "backlinks": 71189488347
}
```

### Interpretation

A higher backlink count indicates a larger link profile, but backlink quality and relevance are more important than quantity alone.

### Common Uses

- Link profile analysis
- Competitor research
- SEO audits

## Referring Domains (`referring_domains`)

### Description

The number of unique domains containing backlinks pointing to the analysed domain or URL.

### Data Type

`integer`

### Example

```json
{
  "referring_domains": 34219158
}
```

### Interpretation

A diverse backlink profile with many unique referring domains is generally considered more valuable than many links from a small number of websites.

## Live Backlinks (`live_backlinks`)

### Description

The number of currently active backlinks discovered by Ahrefs.

### Data Type

`integer`

## All-Time Backlinks (`all_time_backlinks`)

### Description

The total historical number of backlinks discovered by Ahrefs, including backlinks that are no longer active.

### Data Type

`integer`

## Live Referring Domains (`live_referring_domains`)

### Description

The number of currently active referring domains linking to the analysed subdomain.

### Data Type

`integer`

## All-Time Referring Domains (`all_time_referring_domains`)

### Description

The historical number of referring domains discovered by Ahrefs.

### Data Type

`integer`

# Organic Search Metrics

## Organic Traffic (`organic_traffic`)

### Description

Estimated monthly traffic received from organic search results.

### Data Type

`integer`

### Example

```json
{
  "organic_traffic": 1322262400
}
```

### Interpretation

Higher values indicate greater estimated visibility in organic search.

### Common Uses

- Traffic benchmarking
- Competitor analysis
- SEO reporting

### Notes

Traffic values are estimates based on Ahrefs' keyword rankings and search volume data.

## Organic Cost (`organic_cost`)

### Description

Estimated monetary value of organic traffic if equivalent traffic were acquired through paid search advertising.

### Data Type

`integer`

### Unit

**USD cents**

### Example

```json
{
  "organic_cost": 25026940000
}
```

### Interpretation

Higher values indicate organic rankings that would be expensive to replace with paid advertising.

## Organic Keywords (`organic_keywords`)

### Description

The number of keywords for which a website or URL ranks in organic search results.

### Data Type

`integer`

### Example

```json
{
  "organic_keywords": 71972747
}
```

### Common Uses

- Keyword visibility analysis
- Competitor research
- Content strategy

## Organic Keywords Positions 1–3 (`organic_keywords_1_3`)

### Description

The number of organic keywords ranking within the top three search result positions.

### Data Type

`integer`

### Example

```json
{
  "organic_keywords_1_3": 10803366
}
```

### Interpretation

Keywords ranking in positions $1–3$ generally represent the highest-value organic visibility.

# Paid Search Metrics

## Paid Traffic (`paid_traffic`)

### Description

Estimated traffic generated through paid search advertising.

### Data Type

`integer`

## Paid Cost (`paid_cost`)

### Description

Estimated monthly advertising cost required to acquire equivalent paid search traffic.

### Data Type

`integer`

### Unit

**USD cents**

### Example

```json
{
  "paid_cost": 357113658
}
```

## Paid Pages (`paid_pages`)

### Description

The number of pages receiving traffic from paid search campaigns.

### Data Type

`integer`

## Paid Keywords (`paid_keywords`)

### Description

The number of keywords targeted through paid search campaigns.

### Data Type

`integer`

# Usage Notes

## Data Freshness

Ahrefs metrics are generated from Ahrefs' proprietary search index.

Values may change as:

- New backlinks are discovered.
- Existing links disappear.
- Search rankings change.
- Ahrefs updates its database.

## Metric Interpretation

Metrics should be evaluated together.

Examples:

- High Domain Rating with few referring domains may indicate a concentrated backlink profile.
- High backlink counts do not always indicate high-quality links.
- Organic traffic estimates should be compared alongside keyword visibility.

## Best Practices

These metrics are suitable for:

- SEO dashboards
- Competitor benchmarking
- Backlink audits
- Keyword research
- Content planning
- PPC intelligence
- Domain evaluation
