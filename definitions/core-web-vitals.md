# Core Web Vitals Definitions

Comprehensive reference documentation for all performance metrics returned by the **Core Web Vitals** endpoint.

These metrics are generated through automated Lighthouse browser analysis and provide insights into page loading performance, visual stability, rendering behaviour, and user interaction readiness.

# Table of Contents

- [Overview](#overview)
- [Performance Metrics](#performance-metrics)
  - [Lighthouse Performance Score](#lighthouse-performance-score-score)
  - [Time to Interactive](#time-to-interactive-time_to_interactive)
- [Core Web Vitals](#core-web-vitals)
  - [Largest Contentful Paint](#largest-contentful-paint-largest_contentful_paint)
  - [Cumulative Layout Shift](#cumulative-layout-shift-cumulative_layout_shift)
  - [Maximum Potential First Input Delay](#maximum-potential-first-input-delay-max_potential_fid)
- [Paint Metrics](#paint-metrics)
  - [First Contentful Paint](#first-contentful-paint-first_contentful_paint)
  - [Observed First Paint](#observed-first-paint-observed_first_paint)
  - [Observed Largest Contentful Paint](#observed-largest-contentful-paint-observed_largest_contentful_paint)
- [Loading Metrics](#loading-metrics)
  - [Page Load Timing](#page-load-timing-observed_load)
  - [DOM Content Loaded](#dom-content-loaded-observed_dom_content_loaded)
  - [Navigation Start](#navigation-start-observed_navigation_start)
- [Interactivity Metrics](#interactivity-metrics)
  - [Interactive Time](#interactive-time-interactive)
  - [Total Blocking Time](#total-blocking-time-total_blocking_time)
- [Layout Stability Metrics](#layout-stability-metrics)
  - [Main Frame Cumulative Layout Shift](#main-frame-cumulative-layout-shift-cumulative_layout_shift_main_frame)
  - [Observed Cumulative Layout Shift](#observed-cumulative-layout-shift-observed_cumulative_layout_shift)
- [Speed Metrics](#speed-metrics)
  - [Speed Index](#speed-index-speed_index)
  - [Observed Speed Index](#observed-speed-index-observed_speed_index)
- [Trace Timing Metrics](#trace-timing-metrics)
  - [Trace End](#trace-end-observed_trace_end)
  - [Time Origin](#time-origin-observed_time_origin)
  - [Last Visual Change](#last-visual-change-observed_last_visual_change)
- [Usage Notes](#usage-notes)

# Overview

The **Core Web Vitals** endpoint provides technical performance measurements generated through Lighthouse browser analysis.

The metrics measure:

- Page loading speed
- Rendering progress
- User interaction readiness
- Layout stability
- Browser execution performance

The endpoint supports:

- Desktop performance analysis
- Mobile performance analysis

These metrics are commonly used for:

- Technical SEO auditing
- Website performance monitoring
- Core Web Vitals reporting
- Page experience optimisation
- Automated website analysis platforms

Performance values are measured in milliseconds unless otherwise stated.

# Performance Metrics

## Lighthouse Performance Score (`score`)

### Description

The Lighthouse Performance Score is an overall performance rating calculated from multiple Lighthouse performance audits.

### Data Type

`number`

### Range

$0–1$

### Example

```json
{
  "score": 1
}
```

### Interpretation

Higher values indicate better measured performance.

A score closer to $1$ represents stronger Lighthouse performance results.

## Time to Interactive (`time_to_interactive`)

### Description

Time to Interactive measures the time required for a page to become fully usable and responsive to user input.

### Data Type

`integer`

### Unit

Milliseconds

### Example

```json
{
  "time_to_interactive": 464
}
```

### Common Uses

- JavaScript performance analysis
- Interaction readiness monitoring
- Page optimisation

# Core Web Vitals

## Largest Contentful Paint (`largest_contentful_paint`)

### Description

Largest Contentful Paint (LCP) measures the time required for the largest visible content element to render.

Typical LCP elements include:

- Hero images
- Large text blocks
- Main page content

### Data Type

`integer`

### Unit

Milliseconds

### Example

```json
{
  "largest_contentful_paint": 464
}
```

### Interpretation

Lower values indicate faster rendering.

Common thresholds:

| Rating | Value |
|---|---|
| Good | ≤ $2500$ ms |
| Needs Improvement | $2500$–$4000$ ms |
| Poor | > $4000$ ms |

### Common Uses

- User experience analysis
- SEO performance reporting
- Page optimisation

## Cumulative Layout Shift (`cumulative_layout_shift`)

### Description

Cumulative Layout Shift (CLS) measures unexpected visual movement during page loading.

Examples include:

- Images shifting after loading
- Buttons moving unexpectedly
- Content repositioning

### Data Type

`number`

### Range

$0–1$

### Example

```json
{
  "cumulative_layout_shift": 0
}
```

### Interpretation

Lower values indicate better visual stability.

Common thresholds:

| Rating | Value |
|---|---|
| Good | ≤ $0.1$ |
| Needs Improvement | $0.1$–$0.25$ |
| Poor | > $0.25$ |

## Maximum Potential First Input Delay (`max_potential_fid`)

### Description

Maximum Potential First Input Delay estimates the worst-case delay a user may experience when interacting with a page.

### Data Type

`integer`

### Unit

Milliseconds

### Example

```json
{
  "max_potential_fid": 16
}
```

# Paint Metrics

## First Contentful Paint (`first_contentful_paint`)

### Description

First Contentful Paint (FCP) measures when the first piece of visible content appears.

Examples include:

- Text
- Images
- SVG elements

### Data Type

`integer`

### Unit

Milliseconds

## Observed First Paint (`observed_first_paint`)

### Description

The observed timestamp when the browser first renders any visual content.

### Data Type

`integer`

### Unit

Milliseconds

## Observed Largest Contentful Paint (`observed_largest_contentful_paint`)

### Description

The observed Lighthouse measurement of the largest content element rendering time.

### Data Type

`integer`

### Unit

Milliseconds

# Loading Metrics

## Page Load Timing (`observed_load`)

### Description

Measures the time when the browser considers the document fully loaded.

### Data Type

`integer`

### Unit

Milliseconds

## DOM Content Loaded (`observed_dom_content_loaded`)

### Description

Measures when the initial HTML document has been fully parsed and processed.

### Data Type

`integer`

### Unit

Milliseconds

## Navigation Start (`observed_navigation_start`)

### Description

Represents the start point of the browser navigation lifecycle.

### Data Type

`integer`

### Unit

Milliseconds offset

# Interactivity Metrics

## Interactive Time (`interactive`)

### Description

Measures when the page becomes ready for user interaction.

### Data Type

`integer`

### Unit

Milliseconds

## Total Blocking Time (`total_blocking_time`)

### Description

Total Blocking Time (TBT) measures the amount of time the browser main thread is blocked and unable to respond quickly to user input.

### Data Type

`integer`

### Unit

Milliseconds

### Common Uses

- JavaScript performance analysis
- Interaction optimisation
- Technical SEO audits

# Layout Stability Metrics

## Main Frame Cumulative Layout Shift (`cumulative_layout_shift_main_frame`)

### Description

Measures layout instability occurring only within the main document frame.

### Data Type

`number`

### Range

$0–1$

## Observed Cumulative Layout Shift (`observed_cumulative_layout_shift`)

### Description

Observed CLS measurement collected during Lighthouse execution.

### Data Type

`number`

### Range

$0–1$

# Speed Metrics

## Speed Index (`speed_index`)

### Description

Speed Index measures how quickly visible page content is rendered during loading.

### Data Type

`integer`

### Unit

Milliseconds

### Example

```json
{
  "speed_index": 464
}
```

### Interpretation

Lower values indicate faster visual completion.

## Observed Speed Index (`observed_speed_index`)

### Description

The observed Speed Index value collected during browser analysis.

### Data Type

`integer`

### Unit

Milliseconds

# Trace Timing Metrics

## Trace End (`observed_trace_end`)

### Description

The duration endpoint of the Lighthouse performance trace.

### Data Type

`integer`

### Unit

Milliseconds

## Time Origin (`observed_time_origin`)

### Description

The browser performance timing origin used as the reference point for measurements.

### Data Type

`integer`

### Unit

Milliseconds offset

## Last Visual Change (`observed_last_visual_change`)

### Description

The point when the final visible page change occurred during loading.

### Data Type

`integer`

### Unit

Milliseconds

# Usage Notes

## Data Availability

Performance metrics are generated through automated Lighthouse analysis.

Results may vary due to:

- Network conditions
- Server response times
- Browser execution differences
- Dynamic page content

## Device Differences

Desktop and mobile profiles use different performance configurations.

The same URL may produce different results depending on the selected device.

## Recommended Usage

These metrics are suitable for:

- Core Web Vitals monitoring
- Technical SEO reporting
- Performance regression detection
- Website optimisation workflows

## Limitations

- Metrics represent synthetic browser measurements.
- Results may fluctuate between requests.
- Some pages may not expose all metrics due to rendering restrictions.
- Lighthouse scores should be interpreted alongside real-user performance data.