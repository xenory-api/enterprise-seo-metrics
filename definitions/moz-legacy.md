# Moz Legacy Metric Definitions

Comprehensive reference documentation for all SEO metrics returned by the **Moz Legacy Metrics** endpoint.

These metrics originate from Moz's legacy link index and historical authority models. The endpoint is primarily intended for maintaining backwards compatibility with older integrations, historical reporting, and applications that rely on legacy Moz metric definitions.

# Table of Contents

- [Overview](#overview)
- [Authority Metrics](#authority-metrics)
  - [Domain Authority](#domain-authority-domain_authority)
  - [MozRank](#mozrank-moz_rank)
  - [PageRank](#pagerank-page_rank)
  - [Spam Score](#spam-score-spam_score)
  - [Link Propensity](#link-propensity-link_propensity)
- [Backlink Metrics](#backlink-metrics)
  - [Inbound Links](#inbound-links-inbound_links)
  - [Total Backlinks](#total-backlinks-total_backlinks)
  - [Broken Backlinks](#broken-backlinks-broken_backlinks)
  - [Referring Pages](#referring-pages-referring_pages)
  - [Referring Domains](#referring-domains-referring_domains)
  - [Referring Main Domains](#referring-main-domains-referring_main_domains)
  - [Linking Root Domains](#linking-root-domains-linking_root_domains)
- [Usage Notes](#usage-notes)

# Overview

The **Moz Legacy Metrics** endpoint exposes historical SEO metrics and backlink statistics from Moz's legacy index.

Unlike the standard Moz Metrics endpoint, these values are preserved primarily for backwards compatibility with legacy applications and historical reporting workflows. Some metrics use older calculation methods and may differ significantly from their modern counterparts.

These metrics are commonly used for:

- Legacy SEO applications
- Historical reporting
- Migration from older Moz APIs
- Long-term authority comparisons
- Legacy backlink analysis

# Authority Metrics

## Domain Authority (`domain_authority`)

### Description

Legacy Domain Authority estimates the ranking strength of an entire domain using Moz's historical authority model.

Although conceptually similar to the current Domain Authority metric, the underlying calculation methodology may differ.

### Data Type

`integer`

### Range

$0–100$

### Example

```json
{
  "domain_authority": 100
}
```

### Interpretation

Generally:

- Higher values indicate stronger historical domain authority.
- Lower values indicate less established or less authoritative websites.

Because the scoring methodology differs from current Moz metrics, legacy values should not be directly compared with modern Domain Authority scores.

### Common Uses

- Historical reporting
- Legacy application support
- Trend analysis

### Notes

This metric exists primarily for backwards compatibility.

## MozRank (`moz_rank`)

### Description

MozRank is Moz's proprietary link popularity score that measures the relative importance of a webpage or domain based on the quantity and quality of inbound links.

### Data Type

`integer`

### Example

```json
{
  "moz_rank": 934
}
```

### Interpretation

Higher values generally indicate greater link popularity and stronger authority within Moz's legacy index.

### Common Uses

- Historical authority analysis
- Legacy SEO reporting
- Link popularity comparisons

### Notes

MozRank is specific to Moz's historical scoring model and should not be interpreted as Google's PageRank.

## PageRank (`page_rank`)

### Description

PageRank is Moz's legacy approximation of the historical Google PageRank concept. It estimates the relative importance of a website based on its backlink profile.

### Data Type

`number`

### Example

```json
{
  "page_rank": 9.99
}
```

### Interpretation

Higher values generally indicate stronger link popularity and authority.

### Common Uses

- Historical SEO analysis
- Legacy reporting
- Authority comparisons

### Notes

This metric should not be confused with Google's discontinued public PageRank.

## Spam Score (`spam_score`)

### Description

Spam Score estimates the likelihood that a website exhibits characteristics commonly associated with spam or low-quality websites.

### Data Type

`integer`

### Range

$0–100$

### Example

```json
{
  "spam_score": 22
}
```

### Interpretation

- Lower values generally indicate healthier websites.
- Higher values may warrant manual review.

### Common Uses

- Link audits
- Risk assessment
- Backlink quality evaluation

### Notes

Spam Score is intended as an indicator rather than definitive evidence of website quality.

## Link Propensity (`link_propensity`)

### Description

A legacy metric estimating the relative tendency of a website to create outbound links.

### Data Type

`integer`

### Example

```json
{
  "link_propensity": 129
}
```

### Interpretation

Higher values generally indicate websites with stronger outbound linking characteristics.

### Common Uses

- Historical link analysis
- Legacy SEO reporting

### Notes

The exact calculation methodology is proprietary to Moz.

# Backlink Metrics

## Inbound Links (`inbound_links`)

### Description

The total number of inbound links discovered pointing to the analysed website.

### Data Type

`integer`

### Example

```json
{
  "inbound_links": 19444097169
}
```

### Why It Matters

Provides an overall indication of the volume of links pointing to the analysed website.

## Total Backlinks (`total_backlinks`)

### Description

The total number of backlinks identified by Moz's legacy index.

### Data Type

`integer`

### Example

```json
{
  "total_backlinks": 31208291664
}
```

### Why It Matters

Represents the complete backlink count used by the legacy metrics model.

## Broken Backlinks (`broken_backlinks`)

### Description

The number of backlinks that point to URLs which are no longer accessible or return an error.

### Data Type

`integer`

### Example

```json
{
  "broken_backlinks": 667929049
}
```

### Why It Matters

Broken backlinks represent lost link equity and may highlight opportunities for redirects or content restoration.

## Referring Pages (`referring_pages`)

### Description

The number of unique pages that contain one or more backlinks to the analysed website.

### Data Type

`integer`

### Example

```json
{
  "referring_pages": 25503478880
}
```

### Why It Matters

A larger number of referring pages generally indicates broader visibility across the web.

## Referring Domains (`referring_domains`)

### Description

The number of unique domains linking to the analysed website.

### Data Type

`integer`

### Example

```json
{
  "referring_domains": 25912303
}
```

### Why It Matters

Links from a diverse set of domains are generally considered more valuable than many links from the same domain.

## Referring Main Domains (`referring_main_domains`)

### Description

The number of unique main domains that refer traffic or backlinks to the analysed website.

### Data Type

`integer`

### Example

```json
{
  "referring_main_domains": 22429053
}
```

### Why It Matters

This metric provides a higher-level view of backlink diversity by consolidating related subdomains under their primary domain.

## Linking Root Domains (`linking_root_domains`)

### Description

The number of unique root domains linking to the analysed website.

Multiple backlinks from the same website count as a single linking root domain.

### Data Type

`integer`

### Example

```json
{
  "linking_root_domains": 15785699
}
```

### Why It Matters

Search engines generally value backlinks from a diverse range of unique websites.

# Usage Notes

## Legacy Compatibility

These metrics are maintained primarily for applications that depend on historical Moz data structures.

Where possible, new integrations should use the standard **Moz Metrics** endpoint instead.

## Comparing Legacy and Current Metrics

Although several metric names are shared between legacy and modern Moz endpoints, the underlying calculation methods may differ.

For this reason:

- Legacy Domain Authority should not be directly compared with the current Domain Authority.
- Historical MozRank and PageRank values should be interpreted only within the context of legacy reporting.
- Backlink counts may differ because of changes in Moz's crawl coverage and indexing methodology.

## Data Freshness

Legacy metrics are sourced from Moz's historical datasets and may not reflect the latest state of the web.

## Best Practices

These metrics are most appropriate for:

- Maintaining older applications
- Historical SEO analysis
- Legacy reporting
- Migration projects
- Comparing archived SEO datasets
