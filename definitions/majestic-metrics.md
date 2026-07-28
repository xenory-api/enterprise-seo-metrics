# Majestic Metric Definitions

Comprehensive reference documentation for all SEO metrics returned by the **Majestic Metrics** endpoint.

These metrics are sourced from Majestic's backlink index and provide insights into link quality, backlink volume, referring domain diversity, link types, and outbound link context.

# Table of Contents

- [Overview](#overview)
- [Authority Metrics](#authority-metrics)
  - [Trust Flow](#trust-flow-trust_flow)
  - [Citation Flow](#citation-flow-citation_flow)
  - [Trust Metric](#trust-metric-trust_metric)
  - [AC Rank](#ac-rank-ac_rank)
- [Backlink Metrics](#backlink-metrics)
  - [Indexed URLs](#indexed-urls-indexed_urls)
  - [External Backlinks](#external-backlinks-external_backlinks)
  - [Referring Domains](#referring-domains-referring_domains)
- [Link Source Diversity Metrics](#link-source-diversity-metrics)
  - [Educational Backlinks](#educational-backlinks-edu_backlinks)
  - [Educational Exact Backlinks](#educational-exact-backlinks-edu_exact)
  - [Government Backlinks](#government-backlinks-gov_backlinks)
  - [Government Exact Backlinks](#government-exact-backlinks-gov_exact)
  - [Educational Referring Domains](#educational-referring-domains-edu_domains)
  - [Educational Exact Referring Domains](#educational-exact-referring-domains-edu_exact)
  - [Government Referring Domains](#government-referring-domains-gov_domains)
  - [Government Exact Referring Domains](#government-exact-referring-domains-gov_exact)
  - [Referring IPs](#referring-ips-referring_ips)
  - [Referring Subnets](#referring-subnets-referring_subnets)
- [Non-Unique Link Type Metrics](#non-unique-link-type-metrics)
  - [Homepage Links](#homepage-links-homepages)
  - [Indirect Links](#indirect-links-indirect)
  - [Deleted Links](#deleted-links-deleted)
  - [Nofollow Links](#nofollow-links-nofollow)
  - [HTTPS Links](#https-links-https)
  - [Frame Links](#frame-links-frame)
  - [Image Links](#image-links-image)
  - [Redirect Links](#redirect-links-redirect)
  - [Text Links](#text-links-text)
- [Aggregate Link Metrics](#aggregate-link-metrics)
  - [Total Non-Unique Links](#total-non-unique-links-links)
  - [Total Link Types](#total-link-types-types)
- [Outbound Link Context Metrics](#outbound-link-context-metrics)
  - [Internal Links](#internal-links-internal_links)
  - [External Links](#external-links-external_links)
  - [External Domains](#external-domains-external_domains)
- [Usage Notes](#usage-notes)

# Overview

The **Majestic Metrics** endpoint provides backlink intelligence and link profile analysis using Majestic's extensive link index.

The metrics cover several areas:

- Link authority scoring
- Backlink volume
- Referring domain diversity
- Link source quality
- Link type distribution
- Outbound link context

These metrics are commonly used for:

- Backlink profile analysis
- Domain authority evaluation
- Competitor link research
- SEO reporting
- Website auditing
- Link quality assessment

Majestic metrics are generated from proprietary backlink data and should be interpreted as comparative indicators rather than direct search engine ranking signals.

# Authority Metrics

## Trust Flow (`trust_flow`)

### Description

Trust Flow is Majestic's proprietary metric that evaluates the quality of backlinks pointing to a website based on the trustworthiness of linking sources.

The metric is influenced by the quality of websites within the backlink network.

### Data Type

`integer`

### Range

$0–100$

### Example

```json
{
  "trust_flow": 100
}
```

### Interpretation

Generally:

- Higher values indicate backlinks from more trusted sources.
- Lower values indicate weaker or less trusted backlink profiles.

### Common Uses

- Link quality assessment
- Domain comparison
- Backlink auditing

### Notes

Trust Flow measures backlink quality rather than backlink quantity.

## Citation Flow (`citation_flow`)

### Description

Citation Flow measures the influence of a website based on the quantity of backlinks pointing to it.

### Data Type

`integer`

### Range

$0–100$

### Example

```json
{
  "citation_flow": 99
}
```

### Interpretation

Higher values indicate larger backlink volumes.

A high Citation Flow combined with low Trust Flow may indicate a large but potentially lower-quality backlink profile.

### Common Uses

- Backlink volume analysis
- Link profile comparison

## Trust Metric (`trust_metric`)

### Description

Trust Metric is a Majestic trust-based scoring metric evaluating the quality and reliability of backlinks.

### Data Type

`integer`

### Range

$0–100$

### Example

```json
{
  "trust_metric": 100
}
```

## AC Rank (`ac_rank`)

### Description

AC Rank is a legacy Majestic ranking metric that evaluates a website's backlink importance relative to other indexed websites.

### Data Type

`integer`

### Example

```json
{
  "ac_rank": 0
}
```

### Interpretation

Lower rankings generally indicate stronger positions within the Majestic index.

# Backlink Metrics

## Indexed URLs (`indexed_urls`)

### Description

The number of URLs discovered and indexed by Majestic for the analysed domain.

### Data Type

`integer`

### Example

```json
{
  "indexed_urls": 1968165429
}
```

### Common Uses

- Crawl coverage analysis
- Domain scale evaluation

## External Backlinks (`external_backlinks`)

### Description

The total number of external backlinks pointing to the analysed domain or URL.

### Data Type

`integer`

### Example

```json
{
  "external_backlinks": 21890792348
}
```

### Interpretation

Higher values indicate a larger backlink profile, although link quality and relevance remain important factors.

## Referring Domains (`referring_domains`)

### Description

The number of unique domains providing backlinks to the analysed domain.

### Data Type

`integer`

### Example

```json
{
  "referring_domains": 26328259
}
```

### Interpretation

A larger number of unique referring domains generally indicates greater link diversity.

# Link Source Diversity Metrics

## Educational Backlinks (`edu_backlinks`)

### Description

The number of backlinks originating from educational domains.

### Data Type

`integer`

## Educational Exact Backlinks (`edu_exact`)

### Description

The number of backlinks from exact educational domain matches.

### Data Type

`integer`

## Government Backlinks (`gov_backlinks`)

### Description

The number of backlinks originating from government domains.

### Data Type

`integer`

## Government Exact Backlinks (`gov_exact`)

### Description

The number of backlinks from exact government domain matches.

### Data Type

`integer`

## Educational Referring Domains (`edu_domains`)

### Description

The number of unique educational domains linking to the analysed website.

### Data Type

`integer`

## Educational Exact Referring Domains (`edu_exact`)

### Description

The number of exact educational referring domains.

### Data Type

`integer`

## Government Referring Domains (`gov_domains`)

### Description

The number of unique government domains linking to the analysed website.

### Data Type

`integer`

## Government Exact Referring Domains (`gov_exact`)

### Description

The number of exact government referring domains.

### Data Type

`integer`

## Referring IPs (`referring_ips`)

### Description

The number of unique IP addresses associated with referring websites.

### Data Type

`integer`

### Interpretation

Used to evaluate backlink source diversity and identify potential network patterns.

## Referring Subnets (`referring_subnets`)

### Description

The number of unique IP subnets associated with referring websites.

### Data Type

`integer`

# Non-Unique Link Type Metrics

The following metrics describe backlink distribution by link characteristics.

## Homepage Links (`homepages`)

### Description

The number of backlinks originating from homepage URLs.

## Indirect Links (`indirect`)

### Description

The number of backlinks discovered through indirect link relationships.

## Deleted Links (`deleted`)

### Description

The number of backlinks that have been removed or are no longer active.

## Nofollow Links (`nofollow`)

### Description

The number of backlinks marked with the `nofollow` attribute.

## HTTPS Links (`https`)

### Description

The number of backlinks originating from HTTPS URLs.

## Frame Links (`frame`)

### Description

The number of backlinks embedded through frames.

## Image Links (`image`)

### Description

The number of backlinks generated through images.

## Redirect Links (`redirect`)

### Description

The number of backlinks involving redirects.

## Text Links (`text`)

### Description

The number of standard text-based backlinks.

# Aggregate Link Metrics

## Total Non-Unique Links (`links`)

### Description

The total number of non-unique backlinks discovered.

### Data Type

`integer`

## Total Link Types (`types`)

### Description

The total number of link type classifications recorded.

### Data Type

`integer`

# Outbound Link Context Metrics

## Internal Links (`internal_links`)

### Description

The number of outbound links pointing to pages within the same domain.

### Data Type

`integer`

## External Links (`external_links`)

### Description

The number of outbound links pointing to external domains.

### Data Type

`integer`

## External Domains (`external_domains`)

### Description

The number of unique external domains linked from the analysed website.

### Data Type

`integer`

# Usage Notes

## Data Freshness

Majestic metrics may change as:

- New backlinks are discovered.
- Existing links become inactive.
- The Majestic index is refreshed.

## Metric Interpretation

Metrics should be evaluated together.

Examples:

- High Trust Flow with low Citation Flow may indicate a smaller but highly trusted backlink profile.
- High Citation Flow with low Trust Flow may indicate many backlinks from lower-quality sources.
- Referring IP and subnet diversity can help identify unnatural link patterns.

## Best Practices

These metrics are suitable for:

- Backlink auditing
- Competitor analysis
- Domain comparison
- Link quality evaluation
- SEO reporting
- Link profile monitoring