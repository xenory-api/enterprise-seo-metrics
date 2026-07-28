# Anchor Text Analysis Definitions

Comprehensive reference documentation for all anchor text, internal linking, and backlink analysis metrics returned by the **Anchor Text Analysis** endpoint.

The Anchor Text Analysis endpoint provides detailed information about on-page anchor usage, internal and external link structures, backlink anchor distributions, and representative backlink examples.

Unlike individual SEO authority metrics, anchor text analysis focuses on understanding how links are structured and classified across a website's internal pages and external backlink profile.

# Table of Contents

- [Overview](#overview)
- [Page-Level Metrics](#page-level-metrics)
  - [Total Links](#total-links-total_links)
  - [Internal Links](#internal-links-internal)
  - [External Links](#external-links-external)
  - [Anchor Tag Records](#anchor-tag-records-anchor_tags)
- [Anchor Classification Metrics](#anchor-classification-metrics)
  - [Exact Match Anchors](#exact-match-anchors-exact-match)
  - [Partial Match Anchors](#partial-match-anchors-partial-match)
  - [Branded Anchors](#branded-anchors-branded)
  - [Naked URL Anchors](#naked-url-anchors-naked-url)
  - [Generic Anchors](#generic-anchors-generic)
  - [Image Anchors](#image-anchors-image)
  - [Empty Anchors](#empty-anchors-empty)
  - [Other Anchors](#other-anchors-other)
- [Domain-Level Backlink Metrics](#domain-level-backlink-metrics)
  - [Total Backlinks](#total-backlinks-aggregate)
  - [Backlink Anchor Distribution](#backlink-anchor-distribution-distribution)
  - [Percentage Values](#percentage-values)
- [Backlink Example Metrics](#backlink-example-metrics)
  - [Authority Score Backlinks](#authority-score-backlinks)
  - [Domain Rating Backlinks](#domain-rating-backlinks)
- [Data Types](#data-types)
- [Usage Notes](#usage-notes)

# Overview

The **Anchor Text Analysis** endpoint provides SEO insights into how anchor text is used across a website.

The endpoint analyses two primary areas:

- **Page-level anchor analysis** — links extracted directly from the analysed webpage.
- **Domain-level backlink analysis** — external backlinks pointing to the analysed domain.

These metrics can be used for:

- Anchor text auditing
- Internal linking analysis
- Backlink profile evaluation
- Competitor research
- Link building analysis
- SEO reporting dashboards
- Website structure analysis

Anchor text provides search engines and users with contextual information about linked content. Analysing anchor distribution helps identify patterns in internal navigation and external link acquisition.

Metrics should be interpreted collectively rather than individually. A balanced backlink profile typically contains a mixture of branded, topical, generic, and URL-based anchors.

# Page-Level Metrics

The page-level metrics describe links discovered directly on the analysed webpage.

These metrics provide insight into:

- Internal website navigation.
- External references.
- Anchor text distribution.
- Link structure.

## Total Links (`total_links`)

### Description

The total number of hyperlinks discovered on the analysed webpage.

This includes:

- Internal links pointing to the same website.
- External links pointing to third-party websites.

### Data Type

`integer`

### Example

```json
{
  "total_links": 125
}
````

### Interpretation

A higher value indicates a page containing more links.

The number of links should be evaluated in context:

- Large content pages may naturally contain many links.
- Navigation-heavy pages may contain large numbers of internal links.
- Excessive links may indicate poor page structure.

### Common Uses

- Internal linking audits
- Website architecture analysis
- SEO crawling workflows
- Page optimisation reviews

### Related Metrics

- `internal`
- `external`
- `anchor_tags`

## Internal Links (`internal`)

### Description

The number of links pointing to pages within the same domain as the analysed webpage.

Internal links help distribute:

- Navigation signals.
- Page relationships.
- Internal authority flow.

### Data Type

`integer`

### Example

```json
{
  "internal": 85
}
```

### Interpretation

Higher internal link counts may indicate:

- Strong website navigation.
- Better content discoverability.
- More interconnected page structures.

However, excessive internal links may reduce usability or dilute page focus.

### Common Uses

- Internal linking audits
- Site architecture analysis
- Content optimisation
- Technical SEO reviews

### Related Metrics

- `total_links`
- `external`

## External Links (`external`)

### Description

The number of links pointing from the analysed webpage to external domains.

### Data Type

`integer`

### Example

```json
{
  "external": 40
}
```

### Interpretation

External links may provide:

- Additional resources.
- Citations.
- References.
- Contextual relationships.

A high number of external links is not inherently negative and should be evaluated based on relevance and quality.

### Common Uses

- Outbound link audits
- Content quality analysis
- Resource page evaluation

### Related Metrics

- `total_links`
- `internal`

## Anchor Tag Records (`anchor_tags`)

### Description

A collection of individual anchor elements discovered on the analysed page.

Each record represents a single hyperlink and includes information about:

- Destination URL.
- Anchor text.
- Classification.
- Internal/external status.
- Follow attributes.

### Data Type

`array`

### Example

```json
[
  {
    "href": "https://example.com/page",
    "text": "Example page",
    "type": "branded",
    "is_internal": true,
    "is_nofollow": false
  }
]
```

### Fields

| Field         | Type    | Description                                   |
| ------------- | ------- | --------------------------------------------- |
| `href`        | string  | Link destination URL                          |
| `text`        | string  | Visible anchor text                           |
| `type`        | string  | Anchor classification                         |
| `is_internal` | boolean | Whether the link points internally            |
| `is_nofollow` | boolean | Whether the link contains nofollow attributes |

### Common Uses

- Anchor auditing
- Internal linking analysis
- Link classification
- SEO crawling applications

# Anchor Classification Metrics

Anchor classification metrics describe the distribution of anchor text types found within page links or backlink profiles.

## Exact Match Anchors (`exact-match`)

### Description

Represents anchors where the anchor text exactly matches the target keyword or phrase associated with the destination.

### Data Type

`integer`

### Example

```json
{
  "exact-match": 25
}
```

### Interpretation

Higher exact-match usage indicates stronger keyword-focused anchor targeting.

However, excessive exact-match anchors may create an unnatural link profile when compared with other anchor types.

### Common Uses

- Anchor profile analysis
- Competitor comparison
- Link building research

### Related Metrics

- `partial-match`
- `branded`
- `naked-url`

## Partial Match Anchors (`partial-match`)

### Description

Represents anchors that contain variations or related phrases rather than an exact keyword match.

### Data Type

`integer`

### Example

```json
{
  "partial-match": 45
}
```

### Interpretation

Partial-match anchors often provide contextual relevance while maintaining a more natural anchor profile.

### Common Uses

- Keyword targeting analysis
- Content relevance analysis
- Backlink quality evaluation

### Related Metrics

- `exact-match`
- `branded`

## Branded Anchors (`branded`)

### Description

Represents anchors containing a brand name or branded phrase.

Examples include:

- Company names.
- Product names.
- Website names.

### Data Type

`integer`

### Example

```json
{
  "branded": 120
}
```

### Interpretation

Branded anchors are commonly found in natural backlink profiles.

A strong branded anchor presence often indicates organic mentions and brand awareness.

### Common Uses

- Brand visibility analysis
- Backlink profile evaluation
- Competitor research

### Related Metrics

- `exact-match`
- `naked-url`

## Naked URL Anchors (`naked-url`)

### Description

Represents anchors where the visible text is the URL itself.

Examples:

```
https://example.com
example.com
```

### Data Type

`integer`

### Example

```json
{
  "naked-url": 30
}
```

### Interpretation

Naked URL anchors are common in natural citations and references.

### Common Uses

- Backlink diversity analysis
- Natural link profile evaluation

### Related Metrics

- `branded`
- `generic`

## Generic Anchors (`generic`)

### Description

Represents non-descriptive anchor text that does not contain keywords or brand references.

Examples:

- Click here
- Learn more
- Read more

### Data Type

`integer`

### Example

```json
{
  "generic": 15
}
```

### Interpretation

Generic anchors provide limited keyword context but are common in natural linking patterns.

### Common Uses

- Anchor distribution analysis
- Link quality reviews

## Image Anchors (`image`)

### Description

Represents links where the clickable element is an image rather than text.

### Data Type

`integer`

### Example

```json
{
  "image": 8
}
```

### Interpretation

Image links may contribute contextual signals through:

- Image alt text.
- Surrounding content.
- Link placement.

### Common Uses

- Image SEO analysis
- Link structure auditing

## Empty Anchors (`empty`)

### Description

Represents links where no visible anchor text is available.

### Data Type

`integer`

### Example

```json
{
  "empty": 2
}
```

### Interpretation

Empty anchors may indicate:

- Missing text labels.
- Accessibility issues.
- Tracking links.

### Common Uses

- Technical SEO audits
- Accessibility reviews

## Other Anchors (`other`)

### Description

Represents anchor types that do not match the predefined classifications.

### Data Type

`integer`

### Example

```json
{
  "other": 10
}
```

### Common Uses

- Complete anchor distribution analysis
- Unclassified link review

# Domain-Level Backlink Metrics

Domain-level metrics describe backlinks pointing to the analysed domain.

These metrics depend on available backlink index coverage.

## Total Backlinks (`aggregate`)

### Description

The total number of backlinks analysed for the domain.

### Data Type

`integer`

### Example

```json
{
  "aggregate": 7712067120
}
```

### Interpretation

A larger backlink count indicates a larger number of discovered inbound links.

Backlink quantity alone does not determine SEO value. Evaluation should consider:

- Referring domain quality.
- Link relevance.
- Anchor distribution.
- Follow status.

### Common Uses

- Backlink profile analysis
- Competitor comparison
- Link acquisition research

### Related Metrics

- `distribution`
- `domain_rating`
- `authority_score`

## Backlink Anchor Distribution (`distribution`)

### Description

Provides the distribution of backlink anchor types across the analysed backlink profile.

### Data Type

`array`

### Example

```json
[
  {
    "anchor_type": "branded",
    "backlinks": 5000,
    "examples": [
      "Example Brand"
    ]
  }
]
```

### Fields

| Field         | Type    | Description                                |
| ------------- | ------- | ------------------------------------------ |
| `anchor_type` | string  | Anchor classification                      |
| `backlinks`   | integer | Number of backlinks using this anchor type |
| `examples`    | array   | Example anchor text values                 |
| `percentage`  | object  | Distribution percentage information        |

### Common Uses

- Anchor profile monitoring
- Backlink diversity analysis
- Competitor research

# Percentage Values

## Percentage Object (`percentage`)

### Description

Provides scaled percentage information for backlink anchor distribution values.

### Data Type

`object`

### Fields

| Field                 | Type    | Description                   |
| --------------------- | ------- | ----------------------------- |
| `value`               | number  | Raw percentage value          |
| `scaled`              | number  | Scaled percentage value       |
| `scale_unit`          | string  | Percentage unit               |
| `scale_factor`        | integer | Scaling factor                |
| `significant_figures` | integer | Number of significant figures |

### Example

```json
{
  "value": 45.5,
  "scaled": 45.5,
  "scale_unit": "percent",
  "scale_factor": 1,
  "significant_figures": 2
}
```

### Interpretation

Percentage values show the relative proportion of backlinks belonging to each anchor category.

# Backlink Example Metrics

The endpoint provides example backlinks grouped by authority-related metrics.

# Authority Score Backlinks

## Authority Score (`authority_score`)

### Description

The authority score assigned to the referring page containing the backlink.

### Data Type

`integer`

### Example

```json
{
  "authority_score": 78
}
```

### Interpretation

Higher authority scores generally indicate stronger referring pages.

Authority should be evaluated alongside:

- Relevance.
- Link placement.
- Anchor text.
- Traffic value.

### Common Uses

- Backlink quality analysis
- Link prospecting
- Competitor research

## Authority Score Backlink Fields

| Field             | Type    | Description                       |
| ----------------- | ------- | --------------------------------- |
| `authority_score` | integer | Authority score of referring page |
| `referring_text`  | string  | Text surrounding the backlink     |
| `referring_page`  | string  | Referring page URL                |
| `anchor_text`     | string  | Anchor text used                  |
| `anchor_url`      | string  | Destination URL                   |
| `first_seen`      | string  | First discovery timestamp         |
| `last_seen`       | string  | Last discovery timestamp          |

# Domain Rating Backlinks

## Domain Rating (`domain_rating`)

### Description

The authority rating assigned to the referring domain.

### Data Type

`integer`

### Example

```json
{
  "domain_rating": 85
}
```

### Interpretation

Higher domain rating values generally indicate stronger referring domains.

Domain rating should not be considered independently from:

- Relevance.
- Traffic.
- Link context.
- Follow status.

### Common Uses

- Backlink evaluation
- Outreach research
- Competitor analysis

## Domain Rating Backlink Fields

| Field             | Type    | Description                  |
| ----------------- | ------- | ---------------------------- |
| `alt`             | string  | Alternative text             |
| `anchor`          | string  | Anchor text                  |
| `is_dofollow`     | boolean | Whether the link is dofollow |
| `domain_rating`   | integer | Referring domain rating      |
| `organic_traffic` | integer | Estimated organic traffic    |
| `link_type`       | string  | Link type                    |
| `link_context`    | string  | Surrounding link context     |
| `url_from`        | string  | Referring URL                |
| `url_to`          | string  | Destination URL              |
| `first_seen`      | string  | First discovery timestamp    |
| `last_seen`       | string  | Last discovery timestamp     |

# Data Types

| Type    | Description        |
| ------- | ------------------ |
| string  | Text value         |
| integer | Whole number       |
| float   | Decimal number     |
| boolean | True or false      |
| array   | List of values     |
| object  | Nested JSON object |
| null    | Metric unavailable |

# Usage Notes

## Data Availability

Backlink metrics depend on available SEO index coverage.

Some websites may have limited data due to:

- Low backlink volume.
- Recently created pages.
- Limited crawler discovery.

## Interpretation Guidelines

Anchor text metrics should be analysed collectively.

Consider:

- Anchor diversity.
- Referring domain quality.
- Link relevance.
- Link placement.
- Follow attributes.

No single anchor category determines SEO performance.

## Limitations

- Backlink coverage varies by domain.
- Historical timestamps depend on discovery availability.
- Anchor classification is algorithmically determined.
- Metrics should not be interpreted as direct search engine ranking factors.