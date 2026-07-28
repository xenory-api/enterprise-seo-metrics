# Moz Metric Definitions

Comprehensive reference documentation for all SEO metrics returned by the **Moz Metrics** endpoint.

These metrics are sourced from Moz's proprietary search index and are commonly used to evaluate domain authority, backlink profiles, website quality, and overall SEO strength.

# Table of Contents

- [Overview](#overview)
- [Authority Metrics](#authority-metrics)
  - [Domain Authority](#domain-authority-domain_authority)
  - [Page Authority](#page-authority-page_authority)
  - [Spam Score](#spam-score-spam_score)
- [Link Metrics](#link-metrics)
  - [Root Domains Linking](#root-domains-linking-root_domains_linking)
  - [Indirect Root Domains](#indirect-root-domains-indirect_root_domains)
  - [Nofollow Root Domains](#nofollow-root-domains-nofollow_root_domains)
  - [Deleted Root Domains](#deleted-root-domains-deleted_root_domains)
  - [Outbound Domains](#outbound-domains-outbound_domains)
  - [Link Propensity](#link-propensity-link_propensity)
- [Crawl Metrics](#crawl-metrics)
  - [Total Pages](#total-pages-total_pages)
  - [Pages Crawled](#pages-crawled-pages_crawled)
  - [Deleted Pages](#deleted-pages-deleted_pages)
- [Page Metrics](#page-metrics)
  - [External Pages](#external-pages-external_pages)
  - [Nofollow Pages](#nofollow-pages-nofollow_pages)
  - [Outbound Pages](#outbound-pages-outbound_pages)
  - [Redirect Pages](#redirect-pages-redirect_pages)
  - [External Indirect Pages](#external-indirect-pages-external_indirect_pages)
  - [External Nofollow Pages](#external-nofollow-pages-external_nofollow_pages)
  - [External Redirect Pages](#external-redirect-pages-external_redirect_pages)
- [Usage Notes](#usage-notes)

# Overview

The Moz Metrics endpoint returns a collection of SEO metrics describing the authority, popularity, crawl coverage, and linking characteristics of a root domain.

These metrics are widely used for:

- Website authority analysis
- Competitor benchmarking
- Link profile evaluation
- SEO reporting
- Domain quality assessment
- Technical SEO auditing

Because these metrics are generated from Moz's proprietary index, they should be viewed as comparative indicators rather than absolute measurements.

# Authority Metrics

## Domain Authority (`domain_authority`)

### Description

Domain Authority (DA) is Moz's proprietary predictive score that estimates how likely an entire domain is to rank in search engine results relative to other websites.

The score is calculated using numerous link-based signals, including linking root domains, backlink quality, and overall link profile strength.

### Data Type

`integer`

### Range

$0–100$

### Example

```json
{
  "domain_authority": 94
}
```

### Interpretation

Generally:

- Higher values indicate stronger overall domain authority.
- Lower values typically indicate newer or less established websites.

Because the scale is logarithmic, increasing from 70 to 80 is considerably more difficult than increasing from 20 to 30.

### Common Uses

- Domain comparison
- SEO reporting
- Competitor analysis
- Prospect qualification

### Notes

Domain Authority is a comparative metric rather than a Google ranking factor.

## Page Authority (`page_authority`)

### Description

Page Authority (PA) estimates the ranking strength of an individual page using link-based signals.

When returned by this endpoint, it generally represents the authority of the analysed root domain's primary page.

### Data Type

`integer`

### Range

$0–100$

### Example

```json
{
  "page_authority": 91
}
```

### Interpretation

Higher scores indicate stronger ranking potential for the analysed page.

### Common Uses

- Landing page evaluation
- Homepage comparisons
- Link opportunity analysis

## Spam Score (`spam_score`)

### Description

Spam Score estimates the likelihood that a website exhibits characteristics commonly associated with low-quality or spam websites.

### Data Type

`integer`

### Range

$0–100$

### Example

```json
{
  "spam_score": 1
}
```

### Interpretation

Lower scores generally indicate healthier websites.

Higher scores may warrant additional manual review.

### Common Uses

- Link audits
- Backlink evaluation
- Risk assessment

### Notes

Spam Score should never be used as the sole indicator of website quality.

# Link Metrics

## Root Domains Linking (`root_domains_linking`)

### Description

The total number of unique root domains linking to the analysed domain.

Multiple backlinks from the same website count as a single linking root domain.

### Data Type

`integer`

### Example

```json
{
  "root_domains_linking": 1312893
}
```

### Why It Matters

Search engines generally value backlinks from diverse domains more highly than numerous links from a single website.

## Indirect Root Domains (`indirect_root_domains`)

### Description

The number of root domains that link indirectly through redirects or intermediary pages.

## Nofollow Root Domains (`nofollow_root_domains`)

### Description

Unique root domains providing backlinks marked with the `nofollow` attribute.

## Deleted Root Domains (`deleted_root_domains`)

### Description

Root domains that previously linked but are no longer active or available.

## Outbound Domains (`outbound_domains`)

### Description

The number of unique external domains linked from the analysed website.

## Link Propensity (`link_propensity`)

### Description

An estimated probability that pages within the analysed domain naturally contain outbound links.

### Data Type

`number`

### Example

```json
{
    "link_propensity": 0.000010230943
}
```

### Notes

This metric is primarily intended for advanced link analysis.

# Crawl Metrics

## Total Pages (`total_pages`)

### Description

Estimated total number of pages indexed by Moz for the analysed domain.

## Pages Crawled (`pages_crawled`)

### Description

Number of pages successfully crawled and processed within Moz's index.

## Deleted Pages (`deleted_pages`)

### Description

Pages previously discovered that are now unavailable or removed.

# Page Metrics

## External Pages (`external_pages`)

### Description

Pages containing at least one external hyperlink.

## Nofollow Pages (`nofollow_pages`)

### Description

Pages containing one or more nofollow links.

## Outbound Pages (`outbound_pages`)

### Description

Pages containing outbound hyperlinks.

## Redirect Pages (`redirect_pages`)

### Description

Pages that redirect to another destination.

## External Indirect Pages (`external_indirect_pages`)

### Description

Pages containing indirect external links.

## External Nofollow Pages (`external_nofollow_pages`)

### Description

Pages containing external links marked as `nofollow`.

## External Redirect Pages (`external_redirect_pages`)

### Description

Pages containing redirecting external links.

# Usage Notes

## Understanding the Metrics

No single metric should be interpreted in isolation.

For example:

- Domain Authority does not guarantee rankings.
- Spam Score does not indicate penalties.
- Large backlink counts do not necessarily imply higher authority.
- Link quality is generally more important than link quantity.

The most reliable assessments combine multiple metrics to evaluate overall website quality.

## Data Freshness

All metrics are retrieved from Moz's proprietary search index.

Values may change as the index is updated and should be considered point-in-time measurements.

## Best Practices

Use these metrics for:

- SEO reporting
- Domain benchmarking
- Link profile analysis
- Website quality assessment
- Competitor comparisons
- Historical trend monitoring