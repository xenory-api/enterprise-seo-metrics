# Chrome UX Report (CrUX) Definitions

Comprehensive reference documentation for all real-user experience metrics returned by the **Chrome UX Report (CrUX)** endpoint.

Unlike synthetic Lighthouse measurements, CrUX metrics are collected from actual Chrome users and represent field performance data across real browsing environments.

# Table of Contents

- [Overview](#overview)
- [Metric Data Structures](#metric-data-structures)
  - [Histogram Distributions](#histogram-distributions-histogram)
  - [Percentile Values](#percentile-values-percentiles)
- [Core Web Vitals](#core-web-vitals)
  - [Largest Contentful Paint](#largest-contentful-paint-largest_contentful_paint)
  - [First Contentful Paint](#first-contentful-paint-first_contentful_paint)
  - [Cumulative Layout Shift](#cumulative-layout-shift-cumulative_layout_shift)
  - [Interaction to Next Paint](#interaction-to-next-paint-interaction_to_next_paint)
- [Network Performance Metrics](#network-performance-metrics)
  - [Time to First Byte](#time-to-first-byte-experimental_time_to_first_byte)
  - [Round Trip Time](#round-trip-time-round_trip_time)
- [LCP Resource Metrics](#lcp-resource-metrics)
  - [LCP Image Resource Load Delay](#lcp-image-resource-load-delay-largest_contentful_paint_image_resource_load_delay)
  - [LCP Image Resource Load Duration](#lcp-image-resource-load-duration-largest_contentful_paint_image_resource_load_duration)
  - [LCP Image Element Render Delay](#lcp-image-element-render-delay-largest_contentful_paint_image_element_render_delay)
  - [LCP Image Time to First Byte](#lcp-image-time-to-first-byte-largest_contentful_paint_image_time_to_first_byte)
  - [LCP Resource Type](#lcp-resource-type-largest_contentful_paint_resource_type)
- [Device Distribution](#device-distribution)
  - [Form Factors](#form-factors-form_factors)
- [Usage Notes](#usage-notes)

# Overview

The **Chrome UX Report (CrUX)** endpoint provides real-world performance data collected from Chrome browser users.

CrUX differs from synthetic testing tools because metrics represent actual user experiences across:

- Different devices
- Network conditions
- Hardware configurations
- Geographic locations
- Browser environments

CrUX data is commonly used for:

- Real-user Core Web Vitals monitoring
- SEO performance reporting
- Page experience analysis
- Website benchmarking
- Technical optimisation workflows

Metrics are generally represented through:

- Histograms showing user distribution across ranges.
- Percentiles showing aggregate performance thresholds.

# Metric Data Structures

## Histogram Distributions (`histogram`)

### Description

Histogram data represents how users are distributed across predefined performance ranges.

Each histogram bucket contains:

- Start value
- End value
- User density

### Data Type

`array`

### Example

```json
{
  "start": 0,
  "end": 2500,
  "density": 0.757
}
```

### Fields

| Field | Type | Description |
|---|---|---|
| `start` | number/string | Beginning of the metric range |
| `end` | number/string | End of the metric range |
| `density` | number | Fraction of users within this range |

### Interpretation

A density value represents the proportion of users experiencing values within that bucket.

For example:

$0.75$ density means approximately $75\%$ of users fall within that performance range.

## Percentile Values (`percentiles`)

### Description

Percentile values summarise user experience distributions.

The API currently provides the $75$-th percentile (`p75`) value.

### Data Type

`object`

### Fields

| Field | Type | Description |
|---|---|---|
| `p75` | number/string | Metric value experienced by $75\%$ of users |

### Interpretation

The p75 value means:

- $75\%$ of users experienced this value or better.
- $25\%$ of users experienced a worse value.

# Core Web Vitals

## Largest Contentful Paint (`largest_contentful_paint`)

### Description

Largest Contentful Paint (LCP) measures how quickly the largest visible content element is rendered.

Typical LCP elements include:

- Hero images
- Large text blocks
- Main page content

### Data Type

`object`

### Metrics Included

- Histogram distribution
- $75$-th percentile value

### Example

```json
{
  "percentiles": {
    "p75": 2405
  }
}
```

### Unit

Milliseconds

### Interpretation

Common thresholds:

| Rating | Value |
|---|---|
| Good | ≤ $2500$ ms |
| Needs Improvement | $2500$–$4000$ ms |
| Poor | > $4000$ ms |

## First Contentful Paint (`first_contentful_paint`)

### Description

First Contentful Paint (FCP) measures when the first visible page content appears.

Examples include:

- Text
- Images
- SVG elements

### Data Type

`object`

### Unit

Milliseconds

### Interpretation

Lower values indicate faster initial rendering.

## Cumulative Layout Shift (`cumulative_layout_shift`)

### Description

Cumulative Layout Shift (CLS) measures unexpected visual movement during page loading.

Examples include:

- Content shifting after images load.
- Buttons moving after scripts execute.
- Layout changes during rendering.

### Data Type

`object`

### Range

$0–1$

### Interpretation

Common thresholds:

| Rating | Value |
|---|---|
| Good | ≤ $0.1$ |
| Needs Improvement | $0.1$–$0.25$ |
| Poor | > $0.25$ |

## Interaction to Next Paint (`interaction_to_next_paint`)

### Description

Interaction to Next Paint (INP) measures responsiveness after user interactions.

It records the delay between:

1. User interaction.
2. The next visible browser update.

### Data Type

`object`

### Unit

Milliseconds

### Interpretation

Common thresholds:

| Rating | Value |
|---|---|
| Good | ≤ $200$ ms |
| Needs Improvement | $200$–$500$ ms |
| Poor | > $500$ ms |

# Network Performance Metrics

## Time to First Byte (`experimental_time_to_first_byte`)

### Description

Time to First Byte (TTFB) measures the time required for the browser to receive the first byte of data from the server.

It includes:

- Network latency
- Server processing time
- Initial response delivery

### Data Type

`object`

### Unit

Milliseconds

### Interpretation

Lower values indicate faster server response times.

## Round Trip Time (`round_trip_time`)

### Description

Round Trip Time (RTT) measures the network latency between the user and the destination server.

### Data Type

`object`

### Unit

Milliseconds

### Interpretation

Lower RTT values generally indicate faster network communication.

# LCP Resource Metrics

## LCP Image Resource Load Delay (`largest_contentful_paint_image_resource_load_delay`)

### Description

Measures the delay between page loading and the browser beginning to request the LCP image resource.

### Data Type

`object`

### Unit

Milliseconds

### Common Uses

- Image optimisation analysis
- Rendering bottleneck detection

## LCP Image Resource Load Duration (`largest_contentful_paint_image_resource_load_duration`)

### Description

Measures how long the browser takes to download the LCP image resource.

### Data Type

`object`

### Unit

Milliseconds

## LCP Image Element Render Delay (`largest_contentful_paint_image_element_render_delay`)

### Description

Measures the delay between the LCP image becoming available and being displayed.

### Data Type

`object`

### Unit

Milliseconds

## LCP Image Time to First Byte (`largest_contentful_paint_image_time_to_first_byte`)

### Description

Measures server response timing specifically for the LCP image resource.

### Data Type

`object`

### Unit

Milliseconds

## LCP Resource Type (`largest_contentful_paint_resource_type`)

### Description

Shows the distribution of resource types responsible for the largest content element.

### Data Type

`object`

### Fields

| Field | Type | Description |
|---|---|---|
| `fractions.image` | number | Fraction of LCP elements that are images |
| `fractions.text` | number | Fraction of LCP elements that are text |

### Example

```json
{
  "fractions": {
    "image": 0.1688,
    "text": 0.8312
  }
}
```

# Device Distribution

## Form Factors (`form_factors`)

### Description

Provides the distribution of users by device category.

### Data Type

`object`

### Fields

| Field | Type | Description |
|---|---|---|
| `phone` | number | Fraction of phone users |
| `tablet` | number | Fraction of tablet users |
| `desktop` | number | Fraction of desktop users |

### Example

```json
{
  "fractions": {
    "phone": 0.1426,
    "tablet": 0,
    "desktop": 0.8574
  }
}
```

### Interpretation

Values represent the proportion of CrUX users in each device category.

# Usage Notes

## Data Availability

CrUX data availability depends on:

- Sufficient Chrome user traffic.
- Google's inclusion criteria.
- Available historical coverage.

Some URLs may not return data.

## Field Data vs Laboratory Data

CrUX represents real-user field data.

It differs from:

- Lighthouse synthetic testing.
- Controlled browser benchmarks.

Results may differ between CrUX and Core Web Vitals endpoint measurements.

## Recommended Usage

CrUX metrics are suitable for:

- Monitoring real-user performance.
- Tracking Core Web Vitals.
- Comparing websites.
- Building SEO reporting dashboards.
- Measuring user experience trends.

## Limitations

- Low-traffic URLs may not have available data.
- Metrics are aggregated across users.
- Results depend on Chrome UX Report coverage.
- Individual user experiences are not exposed.