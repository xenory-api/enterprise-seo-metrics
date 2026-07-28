# Semrush Metric Definitions

Comprehensive reference documentation for all SEO metrics returned by the **Semrush Metrics** endpoint.

These metrics are sourced from Semrush SEO datasets and provide insights into domain authority, backlink quality, search visibility, traffic distribution, and referring domain characteristics.

# Table of Contents

- [Overview](#overview)
- [Authority Metrics](#authority-metrics)
  - [Authority Score](#authority-score-authority_score)
- [Backlink Metrics](#backlink-metrics)
  - [Total Backlinks](#total-backlinks-total_backlinks)
  - [Referring Domains](#referring-domains-referring_domains)
- [Organic Search Metrics](#organic-search-metrics)
  - [Organic Traffic](#organic-traffic-organic_traffic)
- [Backlink Quality Metrics](#backlink-quality-metrics)
  - [Link Power](#link-power-link_power)
  - [Search Traffic](#search-traffic-search_traffic)
  - [Naturalness](#naturalness-naturalness)
  - [Health](#health-health)
  - [Health v2](#health-v2-health_v2)
  - [Poor Links Indicator](#poor-links-indicator-is_poor_links)
  - [Poor Network Indicator](#poor-network-indicator-is_poor_network)
  - [Poor IP Subnets Indicator](#poor-ip-subnets-indicator-is_poor_ip_subnets)
  - [Poor Referring Domain IP Indicator](#poor-referring-domain-ip-indicator-is_poor_refdomain_ip)
- [Backlink Audit Metrics](#backlink-audit-metrics)
  - [Lost Backlinks](#lost-backlinks-lost_backlinks)
  - [New Backlinks](#new-backlinks-new_backlinks)
  - [New Referring Domains](#new-referring-domains-new_referring_domains)
  - [Lost Referring Domains](#lost-referring-domains-lost_referring_domains)
  - [Last Updated](#last-updated-last_updated)
- [Distribution Metrics](#distribution-metrics)
  - [Organic Traffic Distribution](#organic-traffic-distribution)
  - [Country Traffic Record](#country-traffic-record)
  - [Referring Domain Authority Distribution](#referring-domain-authority-distribution)
  - [Authority Score Distribution Record](#authority-score-distribution-record)
- [Usage Notes](#usage-notes)

# Overview

The **Semrush Metrics** endpoint provides domain-level SEO intelligence from Semrush data sources.

The endpoint combines multiple categories of SEO information:

- Domain authority evaluation
- Backlink profile analysis
- Backlink quality scoring
- Organic search visibility
- Geographic traffic analysis
- Referring domain authority distribution

These metrics are commonly used for:

- SEO reporting platforms
- Competitor analysis tools
- Domain valuation systems
- Marketing intelligence dashboards
- Link profile monitoring
- Search visibility tracking

Semrush metrics are estimates generated from Semrush's proprietary datasets and should be interpreted as comparative indicators rather than absolute measurements.

# Authority Metrics

## Authority Score (`authority_score`)

### Description

Authority Score is Semrush's proprietary metric for evaluating the overall quality and SEO strength of a domain.

The score combines multiple signals, including backlink quality, organic search performance, and domain characteristics.

### Data Type

`integer`

### Range

$0–100$

### Example

```json
{
  "authority_score": 100
}
```

### Interpretation

Generally:

- Higher scores indicate stronger overall domain authority.
- Lower scores indicate weaker SEO signals or less established domains.

### Common Uses

- Domain comparison
- Competitor analysis
- SEO reporting
- Website quality evaluation

### Notes

Authority Score is a Semrush metric and is not a direct search engine ranking factor.

# Backlink Metrics

## Total Backlinks (`total_backlinks`)

### Description

The total number of backlinks pointing to the analysed domain.

A backlink represents an external hyperlink from another website.

### Data Type

`integer`

### Example

```json
{
  "total_backlinks": 45168718551
}
```

### Interpretation

A higher backlink count indicates a larger link profile, but backlink relevance and quality should be evaluated alongside quantity.

### Common Uses

- Backlink analysis
- Competitor research
- Link monitoring

## Referring Domains (`referring_domains`)

### Description

The number of unique domains containing backlinks pointing to the analysed domain.

### Data Type

`integer`

### Example

```json
{
  "referring_domains": 49761505
}
```

### Interpretation

A diverse set of referring domains generally indicates a broader backlink profile.

### Common Uses

- Link diversity analysis
- Authority evaluation
- Competitor comparison

# Organic Search Metrics

## Organic Traffic (`organic_traffic`)

### Description

Estimated monthly traffic generated from organic search results.

### Data Type

`integer`

### Example

```json
{
  "organic_traffic": 4761203167
}
```

### Interpretation

Higher values generally indicate stronger search visibility.

### Common Uses

- SEO performance reporting
- Competitor benchmarking
- Search visibility tracking

### Notes

Traffic values are estimates based on Semrush search data and may differ from first-party analytics platforms.

# Backlink Quality Metrics

## Link Power (`link_power`)

### Description

A score representing the authority and strength of a domain's backlink profile.

### Data Type

`number`

### Interpretation

Higher values generally indicate stronger backlink authority.

## Search Traffic (`search_traffic`)

### Description

A score representing the estimated search visibility and traffic contribution associated with backlinks.

### Data Type

`number`

## Naturalness (`naturalness`)

### Description

A score estimating how natural or organic a backlink profile appears.

### Data Type

`number`

### Interpretation

Higher values generally indicate a more natural backlink profile.

## Health (`health`)

### Description

A backlink health score representing the overall quality condition of the backlink profile.

### Data Type

`number`

## Health v2 (`health_v2`)

### Description

An updated version of the backlink health score using newer Semrush evaluation methods.

### Data Type

`number`

## Poor Links Indicator (`is_poor_links`)

### Description

Indicates whether Semrush has identified signals associated with poor-quality backlinks.

### Data Type

`boolean`

### Example

```json
{
  "is_poor_links": true
}
```

## Poor Network Indicator (`is_poor_network`)

### Description

Indicates whether the backlink profile contains potentially problematic network patterns.

### Data Type

`boolean`

## Poor IP Subnets Indicator (`is_poor_ip_subnets`)

### Description

Indicates whether suspicious IP subnet patterns have been detected among referring sources.

### Data Type

`boolean`

## Poor Referring Domain IP Indicator (`is_poor_refdomain_ip`)

### Description

Indicates whether suspicious IP relationships exist among referring domains.

### Data Type

`boolean`

# Backlink Audit Metrics

## Lost Backlinks (`lost_backlinks`)

### Description

The number of backlinks recently identified as lost.

### Data Type

`integer`

## New Backlinks (`new_backlinks`)

### Description

The number of newly discovered backlinks.

### Data Type

`integer`

## New Referring Domains (`new_referring_domains`)

### Description

The number of newly discovered referring domains.

### Data Type

`integer`

## Lost Referring Domains (`lost_referring_domains`)

### Description

The number of referring domains that are no longer providing backlinks.

### Data Type

`integer`

## Last Updated (`last_updated`)

### Description

Timestamp indicating when the backlink audit data was last refreshed.

### Data Type

`string`

### Example

```json
{
  "last_updated": "2025-01-01T12:00:00Z"
}
```

# Distribution Metrics

## Organic Traffic Distribution

### Description

Provides geographic breakdowns of estimated organic traffic by country.

### Structure

Each record contains:

- ISO country code
- Country name
- Estimated traffic

### Common Uses

- International SEO analysis
- Market identification
- Geographic visibility reporting

## Country Traffic Record

### Description

Represents organic traffic estimates for a specific country.

### Fields

#### Alpha 2 (`alpha_2`)

ISO 3166-1 alpha-2 country code.

### Data Type

`string`

Example:

```json
{
  "alpha_2": "US"
}
```

#### Country (`country`)

Country name associated with the traffic record.

### Data Type

`string`

#### Traffic (`traffic`)

Estimated organic traffic from the specified country.

### Data Type

`integer`

## Referring Domain Authority Distribution

### Description

Groups referring domains by Semrush Authority Score ranges.

### Common Uses

- Backlink quality analysis
- Domain authority distribution analysis
- Link profile evaluation

## Authority Score Distribution Record

### Description

Represents the number of referring domains within a specific Authority Score bucket.

### Fields

#### Authority Score (`authority_score`)

Authority Score bucket value.

### Data Type

`integer`

### Range

$0–100$

#### Referring Domains (`referring_domains`)

Number of referring domains within the Authority Score bucket.

### Data Type

`integer`

# Usage Notes

## Data Freshness

Semrush metrics may change as:

- New backlinks are discovered.
- Existing backlinks disappear.
- Search rankings change.
- Semrush updates its datasets.

## Metric Interpretation

Metrics should be evaluated together.

Examples:

- High Authority Score with low referring domain diversity may indicate concentrated authority.
- High backlink counts do not always indicate high-quality links.
- Traffic estimates should be compared with ranking and keyword data.

## Best Practices

These metrics are suitable for:

- SEO reporting
- Domain evaluation
- Competitor benchmarking
- Backlink audits
- International SEO analysis
- Search visibility monitoring