# Chrome UX Report (CrUX) API

Retrieve real-world user experience metrics collected from Chrome users, including Core Web Vitals distributions, device breakdowns, network performance, and field performance data.

## Overview

The **Chrome UX Report (CrUX) API** provides real-user website performance data from the Chrome User Experience Report dataset.

Unlike synthetic performance testing, CrUX metrics represent actual user experiences collected from Chrome browsers.

Use this endpoint to retrieve:

- Largest Contentful Paint (LCP)
- First Contentful Paint (FCP)
- Cumulative Layout Shift (CLS)
- Interaction to Next Paint (INP)
- Time to First Byte (TTFB)
- Round Trip Time (RTT)
- Device distribution
- LCP resource analysis
- Performance percentiles
- Performance histograms

Common use cases include:

- Real-world Core Web Vitals monitoring
- Website experience reporting
- SEO performance dashboards
- Page experience analysis
- Performance benchmarking
- Technical SEO automation

This endpoint is designed for developers building:

- SEO platforms
- Website auditing tools
- Competitive analysis systems
- Reporting dashboards
- Marketing automation workflows

# HTTP Request

`POST /crux-report`

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
| `url` | string | Yes | Website URL to retrieve Chrome UX Report data for |
| `device` | string | No | Device filter. Defaults to `all`. |

## Available Devices

| Value | Description |
|-------|-------------|
| `all` | Aggregate data across all devices |
| `desktop` | Desktop user experience data |
| `phone` | Mobile phone user experience data |
| `tablet` | Tablet user experience data |

# Example Request

## cURL

```bash
curl --request POST \
  --url https://enterprise-seo-metrics.p.rapidapi.com/crux-report \
  --header "Content-Type: application/x-www-form-urlencoded" \
  --header "x-rapidapi-host: enterprise-seo-metrics.p.rapidapi.com" \
  --header "x-rapidapi-key: YOUR_API_KEY" \
  --data url=https://google.com
```

# Successful Response

```json
{
  "success": true,
  "results": {
    "performance_ms": 113,
    "url": "https://google.com",
    "metrics": {
      "round_trip_time": {
        "histogram": [
          {
            "start": 0,
            "end": 75,
            "density": 0.1999
          },
          {
            "start": 75,
            "end": 275,
            "density": 0.4765
          },
          {
            "start": 275,
            "density": 0.3236
          }
        ],
        "percentiles": {
          "p75": 363
        }
      },
      "cumulative_layout_shift": {
        "histogram": [
          {
            "start": "0.00",
            "end": "0.10",
            "density": 0.9936
          },
          {
            "start": "0.10",
            "end": "0.25",
            "density": 0.002
          },
          {
            "start": "0.25",
            "density": 0.0044
          }
        ],
        "percentiles": {
          "p75": "0.00"
        }
      },
      "largest_contentful_paint": {
        "histogram": [
          {
            "start": 0,
            "end": 2500,
            "density": 0.757
          },
          {
            "start": 2500,
            "end": 4000,
            "density": 0.122
          },
          {
            "start": 4000,
            "density": 0.121
          }
        ],
        "percentiles": {
          "p75": 2405
        }
      },
      "largest_contentful_paint_image_resource_load_delay": {
        "percentiles": {
          "p75": 1047
        }
      },
      "largest_contentful_paint_image_resource_load_duration": {
        "percentiles": {
          "p75": 228
        }
      },
      "largest_contentful_paint_resource_type": {
        "fractions": {
          "image": 0.1688,
          "text": 0.8312
        }
      },
      "experimental_time_to_first_byte": {
        "histogram": [
          {
            "start": 0,
            "end": 800,
            "density": 0.6595
          },
          {
            "start": 800,
            "end": 1800,
            "density": 0.1839
          },
          {
            "start": 1800,
            "density": 0.1566
          }
        ],
        "percentiles": {
          "p75": 1144
        }
      },
      "first_contentful_paint": {
        "histogram": [
          {
            "start": 0,
            "end": 1800,
            "density": 0.6761
          },
          {
            "start": 1800,
            "end": 3000,
            "density": 0.1361
          },
          {
            "start": 3000,
            "density": 0.1879
          }
        ],
        "percentiles": {
          "p75": 2309
        }
      },
      "form_factors": {
        "fractions": {
          "phone": 0.1426,
          "tablet": 0,
          "desktop": 0.8574
        }
      },
      "interaction_to_next_paint": {
        "histogram": [
          {
            "start": 0,
            "end": 200,
            "density": 0.795
          },
          {
            "start": 200,
            "end": 500,
            "density": 0.189
          },
          {
            "start": 500,
            "density": 0.016
          }
        ],
        "percentiles": {
          "p75": 140
        }
      },
      "largest_contentful_paint_image_element_render_delay": {
        "percentiles": {
          "p75": 289
        }
      },
      "largest_contentful_paint_image_time_to_first_byte": {
        "percentiles": {
          "p75": 751
        }
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
| `results` | object | CrUX report response |

# Results Object

| Field | Type | Description |
|-------|------|-------------|
| `performance_ms` | integer | API processing time in milliseconds |
| `url` | string | Analysed URL |
| `metrics` | object | Chrome UX Report metrics |

# Metric Objects

Most CrUX performance metrics return:

- Histogram distributions
- Percentile values

## Histogram Object

Histogram data represents the distribution of users across performance ranges.

| Field | Type | Description |
|-------|------|-------------|
| `start` | number/string | Beginning of metric range |
| `end` | number/string | End of metric range |
| `density` | number | Percentage of users within this range |

Example:

```json
{
  "start": 0,
  "end": 2500,
  "density": 0.757
}
```

## Percentiles Object

| Field | Type | Description |
|-------|------|-------------|
| `p75` | number/string | 75th percentile metric value |

The p75 value represents the threshold experienced by 75% of users.

# Core Web Vitals Metrics

## Largest Contentful Paint (LCP)

Field:

```
largest_contentful_paint
```

Measures loading performance by recording when the largest visible content element is rendered.

| Field | Type | Description |
|-------|------|-------------|
| `histogram` | array | LCP distribution |
| `percentiles.p75` | integer | 75th percentile LCP |

## First Contentful Paint (FCP)

Field:

```
first_contentful_paint
```

Measures the time until the first visible content appears.

| Field | Type | Description |
|-------|------|-------------|
| `histogram` | array | FCP distribution |
| `percentiles.p75` | integer | 75th percentile FCP |

## Cumulative Layout Shift (CLS)

Field:

```
cumulative_layout_shift
```

Measures visual stability by tracking unexpected layout movement.

| Field | Type | Description |
|-------|------|-------------|
| `histogram` | array | CLS distribution |
| `percentiles.p75` | number | 75th percentile CLS |

## Interaction to Next Paint (INP)

Field:

```
interaction_to_next_paint
```

Measures responsiveness after user interactions.

| Field | Type | Description |
|-------|------|-------------|
| `histogram` | array | INP distribution |
| `percentiles.p75` | integer | 75th percentile INP |

## Time To First Byte (TTFB)

Field:

```
experimental_time_to_first_byte
```

Measures server response latency.

| Field | Type | Description |
|-------|------|-------------|
| `histogram` | array | TTFB distribution |
| `percentiles.p75` | integer | 75th percentile TTFB |

## Round Trip Time

Field:

```
round_trip_time
```

Measures network latency between the user and server.

| Field | Type | Description |
|-------|------|-------------|
| `histogram` | array | RTT distribution |
| `percentiles.p75` | integer | 75th percentile RTT |

# LCP Resource Analysis

## LCP Image Resource Load Delay

Field:

```
largest_contentful_paint_image_resource_load_delay
```

Measures the delay before the LCP image resource begins loading.

| Field | Type | Description |
|-------|------|-------------|
| `percentiles.p75` | integer | 75th percentile delay |

## LCP Image Resource Load Duration

Field:

```
largest_contentful_paint_image_resource_load_duration
```

Measures the time required to download the LCP image resource.

## LCP Image Element Render Delay

Field:

```
largest_contentful_paint_image_element_render_delay
```

Measures the delay between resource availability and rendering.

## LCP Image Time To First Byte

Field:

```
largest_contentful_paint_image_time_to_first_byte
```

Measures server response timing for the LCP image.

# LCP Resource Type

Field:

```
largest_contentful_paint_resource_type
```

Provides the distribution of LCP element types.

Example:

```json
{
  "fractions": {
    "image": 0.1688,
    "text": 0.8312
  }
}
```

| Field | Type | Description |
|-------|------|-------------|
| `fractions.image` | number | Percentage of image-based LCP elements |
| `fractions.text` | number | Percentage of text-based LCP elements |

# Device Distribution

Field:

```
form_factors
```

Provides user device distribution.

Example:

```json
{
  "fractions": {
    "phone": 0.1426,
    "tablet": 0,
    "desktop": 0.8574
  }
}
```

| Field | Type | Description |
|-------|------|-------------|
| `phone` | number | Percentage of phone users |
| `tablet` | number | Percentage of tablet users |
| `desktop` | number | Percentage of desktop users |

For detailed explanations of CrUX metrics, see:

```
/definitions/crux.md
```

# Status Codes

| Code | Description |
|------|-------------|
| `200 OK` | CrUX data returned successfully |
| `404 Not Found` | No CrUX data available |
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
      "default": "all",
      "allowed": "all,desktop,phone,tablet"
    }
  }
}
```

## Data Not Found

```json
{
  "success": false,
  "error": {
    "code": 404,
    "status": "NOT_FOUND",
    "message": "CrUX report data not found"
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

# Usage Notes

## Data Availability

- CrUX data is collected from real Chrome users.
- Data availability depends on sufficient traffic volume.
- Some URLs may not have available CrUX records.
- Metrics represent field data rather than synthetic test results.

## Recommended Usage

Recommended scenarios:

- Monitoring real-user Core Web Vitals
- Comparing website experiences
- SEO reporting
- Performance benchmarking
- User experience analysis

## Limitations

- Low-traffic URLs may not return data.
- Metrics are based on aggregated user experiences.
- Results may differ from Lighthouse laboratory tests.
- Historical availability depends on Chrome UX Report coverage.

# Related Endpoints

- Core Web Vitals
- Moz Metrics
- Semrush Metrics
- Majestic Metrics

# Related Definitions

- Largest Contentful Paint (LCP)
- First Contentful Paint (FCP)
- Cumulative Layout Shift (CLS)
- Interaction to Next Paint (INP)
- Time To First Byte (TTFB)
- Chrome UX Report (CrUX)