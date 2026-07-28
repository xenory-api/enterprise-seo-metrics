# Core Web Vitals API

Retrieve website performance metrics based on Lighthouse analysis, including Core Web Vitals, loading performance, interactivity metrics, and layout stability measurements.

## Overview

The **Core Web Vitals API** provides technical website performance metrics for a given URL using automated browser performance analysis.

Use this endpoint to retrieve:

- Performance score
- Largest Contentful Paint (LCP)
- First Contentful Paint (FCP)
- Cumulative Layout Shift (CLS)
- Time to Interactive (TTI)
- Total Blocking Time (TBT)
- Speed Index
- Maximum Potential First Input Delay (FID)
- DOM loading metrics
- Visual rendering timing data

The endpoint supports both desktop and mobile performance analysis.

Common use cases include:

- Technical SEO auditing
- Website performance monitoring
- Core Web Vitals reporting
- Page experience analysis
- Website optimisation workflows
- Automated SEO platforms

This endpoint is designed for developers building:

- SEO platforms
- Website auditing tools
- Competitive analysis systems
- Reporting dashboards
- Marketing automation workflows

# HTTP Request

`POST /core-web-vitals`

# Authentication

This endpoint requires authentication using your RapidAPI subscription credentials.

Required headers:

| Header | Required | Description |
|---------|----------|-------------|
| `x-rapidapi-key` | Yes | Your RapidAPI API key |
| `x-rapidapi-host` | Yes | Enterprise SEO Metrics API host |
| `Content-Type` | Yes | `application/x-www-form-urlencoded` |

For authentication details, see:

```
guides/authentication.md
```

# Request Parameters

## Form Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `url` | string | Yes | URL to analyse (example: `https://google.com`) |
| `device` | string | No | Analysis device profile. Defaults to `desktop`. |

## Available Devices

| Value | Description |
|-------|-------------|
| `desktop` | Desktop Lighthouse performance analysis |
| `mobile` | Mobile Lighthouse performance analysis |

# Example Request

## cURL

```bash
curl --request POST \
  --url https://enterprise-seo-metrics.p.rapidapi.com/core-web-vitals \
  --header "Content-Type: application/x-www-form-urlencoded" \
  --header "x-rapidapi-host: enterprise-seo-metrics.p.rapidapi.com" \
  --header "x-rapidapi-key: YOUR_API_KEY" \
  --data url=https://google.com \
  --data device=desktop
```

# Successful Response

```json
{
  "success": true,
  "results": {
    "performance_ms": 106,
    "url": "https://google.com",
    "metrics": {
      "score": 1,
      "lcp_invalidated": false,
      "time_to_interactive": 464,
      "collected_data": {
        "observed_first_contentful_paint": 394,
        "observed_first_paint": 394,
        "observed_dom_content_loaded": 376,
        "total_blocking_time": 0,
        "observed_last_visual_change_ts": 1142446531467,
        "observed_largest_contentful_paint_all_frames": 394,
        "first_contentful_paint": 464,
        "observed_largest_contentful_paint_ts": 1142446532085,
        "observed_last_visual_change": 393,
        "observed_time_origin_ts": 1142446138467,
        "observed_first_paint_ts": 1142446532085,
        "observed_trace_end_ts": 1142448853010,
        "observed_speed_index": 394,
        "observed_first_visual_change": 393,
        "observed_largest_contentful_paint_all_frames_ts": 1142446532085,
        "largest_contentful_paint": 464,
        "observed_first_contentful_paint_all_frames": 394,
        "observed_cumulative_layout_shift_main_frame": 0,
        "observed_load_ts": 1142446516341,
        "cumulative_layout_shift": 0,
        "observed_first_visual_change_ts": 1142446531467,
        "observed_load": 378,
        "cumulative_layout_shift_main_frame": 0,
        "observed_trace_end": 2715,
        "observed_largest_contentful_paint": 394,
        "observed_speed_index_ts": 1142446532292,
        "observed_navigation_start_ts": 1142446138467,
        "max_potential_fid": 16,
        "observed_dom_content_loaded_ts": 1142446514934,
        "speed_index": 464,
        "interactive": 464,
        "observed_first_contentful_paint_ts": 1142446532085,
        "observed_cumulative_layout_shift": 0,
        "observed_time_origin": 0,
        "observed_first_contentful_paint_all_frames_ts": 1142446532085,
        "observed_navigation_start": 0
      }
    }
  }
}
```

# Response Structure

## Top-Level Fields

| Field | Type | Description |
|-------|------|-------------|
| `success` | boolean | Indicates whether the request completed successfully |
| `results` | object | Core Web Vitals response |

# Results Object

| Field | Type | Description |
|-------|------|-------------|
| `performance_ms` | integer | API processing time in milliseconds |
| `url` | string | Analysed URL |
| `metrics` | object | Performance metrics |

# Metrics Object

| Field | Type | Description |
|-------|------|-------------|
| `score` | number | Lighthouse performance score |
| `lcp_invalidated` | boolean | Indicates whether Largest Contentful Paint data was invalidated |
| `time_to_interactive` | integer | Time until the page becomes interactive in milliseconds |
| `collected_data` | object | Detailed Lighthouse timing measurements |

# Collected Data Object

The `collected_data` object contains detailed browser performance measurements.

## Paint Metrics

| Field | Type | Description |
|-------|------|-------------|
| `first_contentful_paint` | integer | Time until first meaningful content is rendered |
| `observed_first_contentful_paint` | integer | Observed First Contentful Paint |
| `observed_first_contentful_paint_all_frames` | integer | First Contentful Paint across all frames |
| `observed_first_paint` | integer | Time until first paint |
| `largest_contentful_paint` | integer | Largest Contentful Paint timing |
| `observed_largest_contentful_paint` | integer | Observed Largest Contentful Paint |
| `observed_largest_contentful_paint_all_frames` | integer | Largest Contentful Paint across all frames |

## Loading Metrics

| Field | Type | Description |
|-------|------|-------------|
| `observed_load` | integer | Page load timing |
| `observed_load_ts` | integer | Load timestamp |
| `observed_dom_content_loaded` | integer | DOMContentLoaded timing |
| `observed_dom_content_loaded_ts` | integer | DOMContentLoaded timestamp |
| `observed_navigation_start` | integer | Navigation start offset |
| `observed_navigation_start_ts` | integer | Navigation start timestamp |

## Interactivity Metrics

| Field | Type | Description |
|-------|------|-------------|
| `interactive` | integer | Time until page interaction is available |
| `max_potential_fid` | integer | Maximum potential First Input Delay |
| `total_blocking_time` | integer | Total browser main-thread blocking time |

## Layout Stability Metrics

| Field | Type | Description |
|-------|------|-------------|
| `cumulative_layout_shift` | number | Cumulative Layout Shift score |
| `cumulative_layout_shift_main_frame` | number | Main-frame CLS score |
| `observed_cumulative_layout_shift` | number | Observed CLS |
| `observed_cumulative_layout_shift_main_frame` | number | Observed main-frame CLS |

## Speed Metrics

| Field | Type | Description |
|-------|------|-------------|
| `speed_index` | integer | Speed Index score |
| `observed_speed_index` | integer | Observed Speed Index |
| `observed_speed_index_ts` | integer | Speed Index timestamp |

## Trace Timing Data

| Field | Type | Description |
|-------|------|-------------|
| `observed_trace_end` | integer | Trace duration |
| `observed_trace_end_ts` | integer | Trace end timestamp |
| `observed_time_origin` | integer | Performance timing origin |
| `observed_time_origin_ts` | integer | Time origin timestamp |
| `observed_last_visual_change` | integer | Last visible page change |
| `observed_last_visual_change_ts` | integer | Last visual change timestamp |

For detailed explanations of Core Web Vitals metrics, see:

```
/definitions/core-web-vitals.md
```

# Status Codes

| Code | Description |
|------|-------------|
| `200 OK` | Performance metrics returned successfully |
| `422 Unprocessable Entity` | Missing or invalid parameters |
| `500 Internal Server Error` | Unexpected server error |

# Error Responses

## Missing URL

```json
{
  "success": false,
  "error": {
    "code": 422,
    "status": "MISSING_PARAMETER",
    "message": "A valid URL is required"
  }
}
```

## Invalid Device

```json
{
  "success": false,
  "error": {
    "code": 422,
    "status": "INVALID_PARAMETER",
    "message": "Invalid device: <device>",
    "details": {
      "default": "desktop",
      "allowed": "desktop,mobile"
    }
  }
}
```

## Internal Server Error

```json
{
  "success": false,
  "error": {
    "code": 500,
    "status": "UNKNOWN_ERROR",
    "message": "The API threw a JavaScript exception."
  }
}
```

# Error Object

| Field | Type | Description |
|-------|------|-------------|
| `code` | integer | HTTP status code |
| `status` | string | Machine-readable error identifier |
| `message` | string | Human-readable error description |
| `details` | object | Additional validation details |

# Usage Notes

## Data Availability

- Performance metrics are generated through automated browser analysis.
- Results may vary slightly between requests due to network conditions.
- Desktop and mobile results use different browser performance profiles.

## Recommended Usage

Recommended scenarios:

- Core Web Vitals monitoring
- Technical SEO audits
- Page speed reporting
- Performance regression tracking
- Website optimisation workflows

## Limitations

- The endpoint analyses one URL per request.
- Performance values may fluctuate depending on page resources and network conditions.
- Some metrics may be unavailable for pages with rendering restrictions.

# Related Endpoints

- Chrome UX Report
- Moz Metrics
- Semrush Metrics
- Majestic Metrics

# Related Definitions

- Largest Contentful Paint (LCP)
- First Contentful Paint (FCP)
- Cumulative Layout Shift (CLS)
- Time to Interactive (TTI)
- Total Blocking Time (TBT)
- Speed Index