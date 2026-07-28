# Core Web Vitals Response Schema

Comprehensive schema reference for the **Core Web Vitals** endpoint.

This document describes the complete JSON response structure returned by the endpoint, including field names, data types, nullable values, and example payloads.

# Table of Contents

- [Overview](#overview)
- [Successful Response](#successful-response-200)
	- [Response Schema](#response-schema)
	- [Response Structure](#response-structure)
	- [Top-Level Fields](#top-level-fields)
	- [Results Object](#results-object)
	- [Metrics Object](#metrics-object)
		- [Collected Data Object](#collected-data-object)
	- [Data Types](#data-types)
	- [Nullable Fields](#nullable-fields)
	- [Example Response](#example-response)
- [Error Responses](#error-responses)
  - [Validation Error](#validation-error-422)
  - [Server Error](#server-error-500)
- [Notes](#notes)

# Overview

The **Core Web Vitals** endpoint returns Lighthouse-based website performance metrics, including loading performance, responsiveness, interactivity, and layout stability measurements.

The response includes an overall performance score, Core Web Vitals measurements, and detailed browser-collected timing data.

# Successful Response (200)

## Response Schema

```json
{
  "type": "object",
  "properties": {
    "success": {
      "type": "boolean"
    },
    "results": {
      "type": "object",
      "properties": {
        "performance_ms": {
          "type": "integer"
        },
        "url": {
          "type": "string"
        },
        "metrics": {
          "type": "object",
          "properties": {
            "score": {
              "type": "integer"
            },
            "lcp_invalidated": {
              "type": "boolean"
            },
            "time_to_interactive": {
              "type": "integer"
            },
            "collected_data": {
              "type": "object",
              "properties": {
                "observed_first_contentful_paint": {
                  "type": "integer"
                },
                "observed_first_paint": {
                  "type": "integer"
                },
                "observed_dom_content_loaded": {
                  "type": "integer"
                },
                "total_blocking_time": {
                  "type": "integer"
                },
                "observed_last_visual_change_ts": {
                  "type": "integer"
                },
                "observed_largest_contentful_paint_all_frames": {
                  "type": "integer"
                },
                "first_contentful_paint": {
                  "type": "integer"
                },
                "observed_largest_contentful_paint_ts": {
                  "type": "integer"
                },
                "observed_last_visual_change": {
                  "type": "integer"
                },
                "observed_time_origin_ts": {
                  "type": "integer"
                },
                "observed_first_paint_ts": {
                  "type": "integer"
                },
                "observed_trace_end_ts": {
                  "type": "integer"
                },
                "observed_speed_index": {
                  "type": "integer"
                },
                "observed_first_visual_change": {
                  "type": "integer"
                },
                "observed_largest_contentful_paint_all_frames_ts": {
                  "type": "integer"
                },
                "largest_contentful_paint": {
                  "type": "integer"
                },
                "observed_first_contentful_paint_all_frames": {
                  "type": "integer"
                },
                "observed_cumulative_layout_shift_main_frame": {
                  "type": "integer"
                },
                "observed_load_ts": {
                  "type": "integer"
                },
                "cumulative_layout_shift": {
                  "type": "integer"
                },
                "observed_first_visual_change_ts": {
                  "type": "integer"
                },
                "observed_load": {
                  "type": "integer"
                },
                "cumulative_layout_shift_main_frame": {
                  "type": "integer"
                },
                "observed_trace_end": {
                  "type": "integer"
                },
                "observed_largest_contentful_paint": {
                  "type": "integer"
                },
                "observed_speed_index_ts": {
                  "type": "integer"
                },
                "observed_navigation_start_ts": {
                  "type": "integer"
                },
                "max_potential_fid": {
                  "type": "integer"
                },
                "observed_dom_content_loaded_ts": {
                  "type": "integer"
                },
                "speed_index": {
                  "type": "integer"
                },
                "interactive": {
                  "type": "integer"
                },
                "observed_first_contentful_paint_ts": {
                  "type": "integer"
                },
                "observed_cumulative_layout_shift": {
                  "type": "integer"
                },
                "observed_time_origin": {
                  "type": "integer"
                },
                "observed_first_contentful_paint_all_frames_ts": {
                  "type": "integer"
                },
                "observed_navigation_start": {
                  "type": "integer"
                }
              }
            }
          }
        }
      }
    }
  }
}
```

## Response Structure

```text
Response
├── success
└── results
    ├── performance_ms
    ├── url
    └── metrics
        ├── score
        ├── lcp_invalidated
        ├── time_to_interactive
        └── collected_data
            ├── observed_first_contentful_paint
            ├── observed_first_paint
            ├── observed_dom_content_loaded
            ├── total_blocking_time
            ├── observed_last_visual_change_ts
            ├── observed_largest_contentful_paint_all_frames
            ├── first_contentful_paint
            ├── observed_largest_contentful_paint_ts
            ├── observed_last_visual_change
            ├── observed_time_origin_ts
            ├── observed_first_paint_ts
            ├── observed_trace_end_ts
            ├── observed_speed_index
            ├── observed_first_visual_change
            ├── observed_largest_contentful_paint_all_frames_ts
            ├── largest_contentful_paint
            ├── observed_first_contentful_paint_all_frames
            ├── observed_cumulative_layout_shift_main_frame
            ├── observed_load_ts
            ├── cumulative_layout_shift
            ├── observed_first_visual_change_ts
            ├── observed_load
            ├── cumulative_layout_shift_main_frame
            ├── observed_trace_end
            ├── observed_largest_contentful_paint
            ├── observed_speed_index_ts
            ├── observed_navigation_start_ts
            ├── max_potential_fid
            ├── observed_dom_content_loaded_ts
            ├── speed_index
            ├── interactive
            ├── observed_first_contentful_paint_ts
            ├── observed_cumulative_layout_shift
            ├── observed_time_origin
            ├── observed_first_contentful_paint_all_frames_ts
            └── observed_navigation_start
```

## Top-Level Fields

| Field | Type | Nullable | Description |
|------|------|----------|-------------|
| success | Boolean | No | Indicates whether the request completed successfully. |
| results | Object | No | Contains the Core Web Vitals response data. |

## Results Object

| Field | Type | Nullable | Description |
|------|------|----------|-------------|
| performance_ms | Integer | No | Server processing time in milliseconds. |
| url | String | No | URL analysed by the endpoint. |
| metrics | Object | No | Collection of website performance metrics. |

## Metrics Object

| Field | Type | Nullable | Description |
|------|------|----------|-------------|
| score | Integer | No | Lighthouse performance score. |
| lcp_invalidated | Boolean | No | Indicates whether Largest Contentful Paint data was invalidated. |
| time_to_interactive | Integer | No | Time required for the page to become fully interactive. |
| collected_data | Object | No | Detailed browser-collected performance timing data. |

## Collected Data Object

| Field | Type | Nullable | Description |
|------|------|----------|-------------|
| observed_first_contentful_paint | Integer | No | Time until the first contentful paint was observed. |
| observed_first_paint | Integer | No | Time until the first paint event. |
| observed_dom_content_loaded | Integer | No | Time until the DOM content loaded event. |
| total_blocking_time | Integer | No | Total time the main thread was blocked. |
| observed_largest_contentful_paint_all_frames | Integer | No | Largest Contentful Paint across all frames. |
| largest_contentful_paint | Integer | No | Largest Contentful Paint measurement. |
| cumulative_layout_shift | Integer | No | Cumulative Layout Shift measurement. |
| cumulative_layout_shift_main_frame | Integer | No | CLS measurement for the main frame. |
| max_potential_fid | Integer | No | Maximum potential First Input Delay. |
| first_contentful_paint | Integer | No | First Contentful Paint measurement. |
| speed_index | Integer | No | Speed Index measurement. |
| interactive | Integer | No | Time until the page becomes interactive. |
| observed_speed_index | Integer | No | Observed Speed Index value. |
| observed_navigation_start | Integer | No | Navigation start timestamp. |
| observed_navigation_start_ts | Integer | No | Navigation start timestamp in trace format. |
| observed_load | Integer | No | Page load timing value. |
| observed_load_ts | Integer | No | Page load timestamp. |
| observed_trace_end | Integer | No | Trace completion time. |
| observed_trace_end_ts | Integer | No | Trace completion timestamp. |
| observed_time_origin | Integer | No | Browser time origin. |
| observed_time_origin_ts | Integer | No | Browser time origin timestamp. |
| observed_first_paint_ts | Integer | No | First paint timestamp. |
| observed_first_contentful_paint_ts | Integer | No | First Contentful Paint timestamp. |
| observed_first_contentful_paint_all_frames | Integer | No | First Contentful Paint across all frames. |
| observed_first_contentful_paint_all_frames_ts | Integer | No | First Contentful Paint timestamp across all frames. |
| observed_first_visual_change | Integer | No | First visual change timing. |
| observed_first_visual_change_ts | Integer | No | First visual change timestamp. |
| observed_last_visual_change | Integer | No | Last visual change timing. |
| observed_last_visual_change_ts | Integer | No | Last visual change timestamp. |
| observed_largest_contentful_paint | Integer | No | Observed Largest Contentful Paint value. |
| observed_largest_contentful_paint_ts | Integer | No | Largest Contentful Paint timestamp. |
| observed_largest_contentful_paint_all_frames_ts | Integer | No | Largest Contentful Paint timestamp across all frames. |
| observed_dom_content_loaded_ts | Integer | No | DOM Content Loaded timestamp. |
| observed_cumulative_layout_shift | Integer | No | Observed CLS value. |
| observed_cumulative_layout_shift_main_frame | Integer | No | Observed main-frame CLS value. |
| observed_speed_index_ts | Integer | No | Speed Index timestamp. |

## Data Types

The Enterprise SEO Metrics API uses the following JSON data types.

| Type | Description | Example |
|------|-------------|---------|
| String | UTF-8 encoded text | `"https://google.com"` |
| Integer | Whole number | `2500` |
| Boolean | Logical value | `true` |
| Object | JSON object | `{}` |

## Nullable Fields

The Core Web Vitals endpoint does not currently return nullable fields in successful responses.

Applications should still be designed to safely handle new optional fields that may be introduced in future API versions.

## Example Response

```json
{
  "success": true,
  "results": {
    "performance_ms": 842,
    "url": "https://google.com",
    "metrics": {
      "score": 95,
      "lcp_invalidated": false,
      "time_to_interactive": 3200,
      "collected_data": {
        "first_contentful_paint": 1200,
        "largest_contentful_paint": 2100,
        "cumulative_layout_shift": 0,
        "max_potential_fid": 100,
        "speed_index": 1800,
        "interactive": 3200,
        "total_blocking_time": 50
      }
    }
  }
}
```

# Error Responses

Both validation and server errors follow a consistent response structure.

## Schema

```json
{
  "type": "object",
  "properties": {
    "success": {
      "type": "boolean"
    },
    "error": {
      "type": "object",
      "properties": {
        "code": {
          "type": "integer"
        },
        "status": {
          "type": "string"
        },
        "message": {
          "type": "string"
        }
      }
    }
  }
}
```

## Validation Error (422)

Returned when the request contains invalid or missing parameters.

### Schema

```json
{
  "type": "object",
  "properties": {
    "success": {
      "type": "boolean"
    },
    "error": {
      "type": "object",
      "properties": {
        "code": {
          "type": "integer"
        },
        "status": {
          "type": "string"
        },
        "message": {
          "type": "string"
        },
        "details": {
          "type": "object",
          "properties": {
            "default": {
              "type": "string"
            },
            "allowed": {
              "type": "string"
            }
          }
        }
      }
    }
  }
}
```

### Error Object

| Field | Type | Nullable | Description |
|------|------|----------|-------------|
| code | Integer | No | HTTP status code. |
| status | String | No | Error status identifier. |
| message | String | No | Human-readable description of the validation error. |
| details | Object | Yes | Additional validation information. |

### Details Object

| Field | Type | Nullable | Description |
|------|------|----------|-------------|
| default | String | Yes | Default value or expected parameter format. |
| allowed | String | Yes | Allowed values for the parameter. |

### Example

```json
{
  "success": false,
  "error": {
    "code": 422,
    "status": "Unprocessable Entity",
    "message": "Invalid URL parameter."
  }
}
```

## Server Error (500)

Returned when an unexpected server error occurs.

### Schema

See the general error schema above.

### Error Object

| Field | Type | Nullable | Description |
|------|------|----------|-------------|
| code | Integer | No | HTTP status code. |
| status | String | No | Error status identifier. |
| message | String | No | Human-readable description of the server error. |

### Example

```json
{
  "success": false,
  "error": {
    "code": 500,
    "status": "Internal Server Error",
    "message": "An unexpected error occurred while processing the request."
  }
}
```

# Notes

- Fields are documented in the order they appear in the API response.
- All data types follow standard JSON conventions.
- Metric definitions are documented separately in `/definitions/core-web-vitals.md`.
- Applications should ignore unknown fields to ensure forward compatibility with future API versions.