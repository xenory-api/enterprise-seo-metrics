# Social Shares Metric Definitions

Comprehensive reference documentation for all social engagement metrics returned by the **Social Shares** endpoint.

These metrics represent publicly available social sharing activity for a URL across supported social platforms. They are intended to help developers, marketers, and SEO professionals measure content distribution, social engagement, and link popularity.

# Table of Contents

- [Overview](#overview)
- [Social Share Metrics](#social-share-metrics)
  - [Facebook Shares](#facebook-shares-facebook)
  - [Buffer Shares](#buffer-shares-buffer)
  - [Pinterest Shares](#pinterest-shares-pinterest)
  - [Tumblr Shares](#tumblr-shares-tumblr)
  - [VK Shares](#vk-shares-vk)
  - [Odnoklassniki Shares](#odnoklassniki-shares-odnoklassniki)
- [Usage Notes](#usage-notes)

# Overview

The **Social Shares** endpoint provides aggregated social engagement metrics for individual URLs.

Unlike SEO authority or backlink metrics, social share counts measure how frequently content has been shared across supported social platforms.

These metrics are commonly used for:

- Content performance analysis
- Social engagement reporting
- SEO content audits
- Competitor content research
- Link popularity analysis
- Marketing analytics dashboards

The endpoint currently provides share counts from:

- Facebook
- Buffer
- Pinterest
- Tumblr
- VK
- Odnoklassniki

# Social Share Metrics

## Facebook Shares (`facebook`)

### Description

The total number of recorded Facebook shares associated with the analysed URL.

Facebook shares represent how many times a page has been distributed through Facebook's sharing ecosystem.

### Data Type

`integer`

### Example

```json
{
  "facebook": 60243731
}
````

### Interpretation

Higher values generally indicate stronger social distribution and audience engagement on Facebook.

A high Facebook share count may suggest:

- Strong content visibility
- High audience interest
- Effective social promotion
- Increased potential for referral traffic

### Common Uses

- Measuring content virality
- Comparing competitor content performance
- Identifying highly shared pages
- Building social engagement reports

### Notes

Facebook share availability depends on publicly accessible platform data and may vary based on Facebook indexing and API availability.

## Buffer Shares (`buffer`)

### Description

The total number of recorded Buffer shares associated with the analysed URL.

Buffer is a social media management platform that allows users to schedule and distribute content across multiple networks.

### Data Type

`integer`

### Example

```json
{
  "buffer": 14813
}
```

### Interpretation

Higher values indicate that a URL has been shared more frequently through Buffer's distribution platform.

This may indicate:

- Strong content promotion activity
- Use within marketing workflows
- Higher social distribution volume

### Common Uses

- Content marketing analysis
- Social distribution tracking
- Competitor research

### Notes

Buffer share counts represent activity recorded through the Buffer platform and may not represent total social shares across all networks.

## Pinterest Shares (`pinterest`)

### Description

The total number of recorded Pinterest shares associated with the analysed URL.

Pinterest shares represent how frequently content has been saved or distributed through Pinterest.

### Data Type

`integer`

### Example

```json
{
  "pinterest": 64
}
```

### Interpretation

Higher values may indicate strong visual content engagement or content popularity within Pinterest audiences.

### Common Uses

- Measuring visual content performance
- Tracking content distribution
- Identifying popular resources

### Notes

Pinterest activity is highly dependent on content type, audience, and platform indexing.

## Tumblr Shares (`tumblr`)

### Description

The total number of recorded Tumblr shares associated with the analysed URL.

Tumblr shares represent content distribution activity through the Tumblr blogging platform.

### Data Type

`integer`

### Example

```json
{
  "tumblr": 1087
}
```

### Interpretation

Higher values indicate greater sharing activity within Tumblr communities.

### Common Uses

- Social engagement reporting
- Historical content analysis
- Competitor research

### Notes

Tumblr share counts may vary depending on platform availability and indexing coverage.

## VK Shares (`vk`)

### Description

The total number of recorded VK shares associated with the analysed URL.

VK shares represent content distribution activity through VK, a major social network primarily used in Russian-speaking markets.

### Data Type

`integer`

### Example

```json
{
  "vk": 303365
}
```

### Interpretation

Higher values indicate stronger engagement from VK audiences.

### Common Uses

- Regional content analysis
- International social reporting
- Social popularity comparisons

### Notes

VK share availability depends on publicly accessible platform data.

## Odnoklassniki Shares (`odnoklassniki`)

### Description

The total number of recorded Odnoklassniki shares associated with the analysed URL.

Odnoklassniki shares represent content distribution activity through the Odnoklassniki social network.

### Data Type

`integer`

### Example

```json
{
  "odnoklassniki": 1298
}
```

### Interpretation

Higher values indicate stronger engagement among Odnoklassniki users.

### Common Uses

- Regional audience analysis
- Social engagement reporting
- Content popularity measurement

### Notes

Availability may vary depending on platform indexing and publicly accessible share information.

# Usage Notes

## Interpreting Social Share Counts

Social share counts should be treated as engagement indicators rather than direct SEO ranking factors.

A high number of shares may indicate:

- Strong audience interest
- Effective content promotion
- Greater content visibility
- Potential referral traffic opportunities

However, social shares do not directly measure:

- Search engine rankings
- Backlink authority
- Organic traffic
- Conversion performance

## Data Availability

Social share counts are collected from publicly available platform data.

Metric availability depends on:

- Social platform accessibility
- URL indexing status
- Platform-specific update frequency
- Changes to social network APIs or sharing systems

Counts may differ between platforms because each network tracks engagement differently.

## Best Practices

Social share metrics are most useful when combined with:

- Backlink metrics
- Organic traffic data
- Content performance analytics
- SEO visibility metrics
- Engagement measurements

Recommended applications include:

- Identifying high-performing content
- Comparing competitor pages
- Evaluating content promotion strategies
- Building marketing dashboards
- Monitoring social distribution trends