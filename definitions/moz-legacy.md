# Moz Legacy Metric Definitions

Comprehensive reference documentation for all SEO metrics returned by the **Moz Legacy Metrics** endpoint.

These metrics originate from Moz's legacy link index and historical authority models. The endpoint is primarily intended for maintaining backwards compatibility with older integrations, historical reporting, and applications that rely on legacy Moz metric definitions.

# Table of Contents

- [Overview](#overview)
- [Authority Metrics](#authority-metrics)
  - [Domain Authority](#domain-authority-domain_authority)
  - [PageRank](#pagerank-page_rank)
  - [Spam Score](#spam-score-spam_score)
  - [Link Propensity](#link-propensity-link_propensity)
- [Subdomain Link Metrics](#subdomain-link-metrics)
  - [Pages to Subdomain](#pages-to-subdomain-pages_to_subdomain)
  - [External Pages to Subdomain](#external-pages-to-subdomain-external_pages_to_subdomain)
  - [Nofollow Pages to Subdomain](#nofollow-pages-to-subdomain-nofollow_pages_to_subdomain)
  - [Redirect Pages to Subdomain](#redirect-pages-to-subdomain-redirect_pages_to_subdomain)
  - [External Nofollow Pages to Subdomain](#external-nofollow-pages-to-subdomain-external_nofollow_pages_to_subdomain)
  - [External Redirect Pages to Subdomain](#external-redirect-pages-to-subdomain-external_redirect_pages_to_subdomain)
  - [Deleted Pages to Subdomain](#deleted-pages-to-subdomain-deleted_pages_to_subdomain)
- [Root Domain Metrics](#root-domain-metrics)
  - [Root Domains to Subdomain](#root-domains-to-subdomain-root_domains_to_subdomain)
  - [Deleted Root Domains to Subdomain](#deleted-root-domains-to-subdomain-deleted_root_domains_to_subdomain)
  - [Nofollow Root Domains to Subdomain](#nofollow-root-domains-to-subdomain-nofollow_root_domains_to_subdomain)
- [Usage Notes](#usage-notes)

# Overview

The **Moz Legacy Metrics** endpoint exposes historical SEO metrics and backlink statistics from Moz's legacy index.

Unlike the standard Moz Metrics endpoint, these values are preserved primarily for backwards compatibility with legacy applications and historical reporting workflows. Some metrics use older calculation methodologies and may differ significantly from their modern counterparts.

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

# Subdomain Link Metrics

## Pages to Subdomain (`pages_to_subdomain`)

### Description

The total number of pages linking to the analysed subdomain.

### Data Type

`integer`

### Example

```json
{
  "pages_to_subdomain": 19444097169
}
```

### Why It Matters

Provides an indication of the overall backlink footprint pointing towards the analysed subdomain.

## External Pages to Subdomain (`external_pages_to_subdomain`)

### Description

The number of external pages linking to the analysed subdomain.

## Nofollow Pages to Subdomain (`nofollow_pages_to_subdomain`)

### Description

The number of linking pages containing backlinks marked with the `nofollow` attribute.

## Redirect Pages to Subdomain (`redirect_pages_to_subdomain`)

### Description

The number of linking pages that redirect visitors to the analysed subdomain.

## External Nofollow Pages to Subdomain (`external_nofollow_pages_to_subdomain`)

### Description

The number of external pages linking via `nofollow` backlinks.

## External Redirect Pages to Subdomain (`external_redirect_pages_to_subdomain`)

### Description

The number of external redirecting pages pointing to the analysed subdomain.

## Deleted Pages to Subdomain (`deleted_pages_to_subdomain`)

### Description

Previously discovered linking pages that have since been removed or are no longer accessible.

### Why It Matters

A high value may indicate historical link loss over time.

# Root Domain Metrics

## Root Domains to Subdomain (`root_domains_to_subdomain`)

### Description

The number of unique root domains linking to the analysed subdomain.

Multiple backlinks from the same website count as a single linking root domain.

### Data Type

`integer`

### Example

```json
{
  "root_domains_to_subdomain": 15785699
}
```

### Why It Matters

Search engines generally value backlinks from a diverse range of unique websites.

## Deleted Root Domains to Subdomain (`deleted_root_domains_to_subdomain`)

### Description

Root domains that previously linked to the analysed subdomain but are no longer active or available.

## Nofollow Root Domains to Subdomain (`nofollow_root_domains_to_subdomain`)

### Description

Unique root domains providing backlinks exclusively marked with the `nofollow` attribute.

# Usage Notes

## Legacy Compatibility

These metrics are maintained primarily for applications that depend on historical Moz data structures.

Where possible, new integrations should use the standard **Moz Metrics** endpoint instead.

## Comparing Legacy and Current Metrics

Although several metric names are shared between legacy and modern Moz endpoints, the underlying calculation methods may differ.

For this reason:

- Legacy Domain Authority should not be directly compared with the current Domain Authority.
- Historical PageRank values should be interpreted only within the context of legacy reporting.
- Link counts may differ because of changes in Moz's crawl coverage and indexing methodology.

## Data Freshness

Legacy metrics are sourced from Moz's historical datasets and may not reflect the latest state of the web.

## Best Practices

These metrics are most appropriate for:

- Maintaining older applications
- Historical SEO analysis
- Legacy reporting
- Migration projects
- Comparing archived SEO datasets