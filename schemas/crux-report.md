# Chrome UX Report Response Schema

Comprehensive schema reference for the **Chrome UX Report (CrUX)** endpoint.

This document describes the complete JSON response structure returned by the endpoint, including field names, data types, nullable values, and example payloads.

# Table of Contents

- [Overview](#overview)
- [Successful Response](#successful-response-200)
	- [Response Schema](#response-schema)
	- [Response Structure](#response-structure)
	- [Top-Level Fields](#top-level-fields)
	- [Results Object](#results-object)
	- [Metrics Object](#metrics-object)
		- [Histogram Object](#histogram-object)
		- [Percentiles Object](#percentiles-object)
		- [Fractions Object](#fractions-object)
	- [Data Types](#data-types)
	- [Nullable Fields](#nullable-fields)
	- [Example Response](#example-response)
- [Error Responses](#error-responses)
  - [Validation Error](#validation-error-422)
  - [Not Found Error](#not-found-error-404)
  - [Server Error](#server-error-500)
- [Notes](#notes)

# Overview

The **Chrome UX Report (CrUX)** endpoint returns real-user website experience metrics collected from actual Chrome users.

The response includes Core Web Vitals metrics, performance distributions, device breakdowns, and detailed percentile measurements based on field data from the Chrome UX Report dataset.

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
            "round_trip_time": {
              "type": "object",
              "properties": {
                "histogram": {
                  "type": "array",
                  "items": {
                    "type": "object"
                  }
                },
                "percentiles": {
                  "type": "object",
                  "properties": {
                    "p75": {
                      "type": "integer"
                    }
                  }
                }
              }
            },
            "cumulative_layout_shift": {
              "type": "object",
              "properties": {
                "histogram": {
                  "type": "array",
                  "items": {
                    "type": "object"
                  }
                },
                "percentiles": {
                  "type": "object",
                  "properties": {
                    "p75": {
                      "type": "string"
                    }
                  }
                }
              }
            },
            "largest_contentful_paint": {
              "type": "object",
              "properties": {
                "histogram": {
                  "type": "array",
                  "items": {
                    "type": "object"
                  }
                },
                "percentiles": {
                  "type": "object",
                  "properties": {
                    "p75": {
                      "type": "integer"
                    }
                  }
                }
              }
            },
            "largest_contentful_paint_image_resource_load_delay": {
              "type": "object",
              "properties": {
                "percentiles": {
                  "type": "object",
                  "properties": {
                    "p75": {
                      "type": "integer"
                    }
                  }
                }
              }
            },
            "largest_contentful_paint_image_resource_load_duration": {
              "type": "object",
              "properties": {
                "percentiles": {
                  "type": "object",
                  "properties": {
                    "p75": {
                      "type": "integer"
                    }
                  }
                }
              }
            },
            "largest_contentful_paint_resource_type": {
              "type": "object",
              "properties": {
                "fractions": {
                  "type": "object",
                  "properties": {
                    "image": {
                      "type": "number"
                    },
                    "text": {
                      "type": "number"
                    }
                  }
                }
              }
            },
            "experimental_time_to_first_byte": {
              "type": "object",
              "properties": {
                "histogram": {
                  "type": "array",
                  "items": {
                    "type": "object"
                  }
                },
                "percentiles": {
                  "type": "object",
                  "properties": {
                    "p75": {
                      "type": "integer"
                    }
                  }
                }
              }
            },
            "first_contentful_paint": {
              "type": "object",
              "properties": {
                "histogram": {
                  "type": "array",
                  "items": {
                    "type": "object"
                  }
                },
                "percentiles": {
                  "type": "object",
                  "properties": {
                    "p75": {
                      "type": "integer"
                    }
                  }
                }
              }
            },
            "form_factors": {
              "type": "object",
              "properties": {
                "fractions": {
                  "type": "object",
                  "properties": {
                    "phone": {
                      "type": "number"
                    },
                    "tablet": {
                      "type": "integer"
                    },
                    "desktop": {
                      "type": "number"
                    }
                  }
                }
              }
            },
            "interaction_to_next_paint": {
              "type": "object",
              "properties": {
                "histogram": {
                  "type": "array",
                  "items": {
                    "type": "object"
                  }
                },
                "percentiles": {
                  "type": "object",
                  "properties": {
                    "p75": {
                      "type": "integer"
                    }
                  }
                }
              }
            },
            "largest_contentful_paint_image_element_render_delay": {
              "type": "object",
              "properties": {
                "percentiles": {
                  "type": "object",
                  "properties": {
                    "p75": {
                      "type": "integer"
                    }
                  }
                }
              }
            },
            "largest_contentful_paint_image_time_to_first_byte": {
              "type": "object",
              "properties": {
                "percentiles": {
                  "type": "object",
                  "properties": {
                    "p75": {
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
        ├── round_trip_time
        │   ├── histogram
        │   └── percentiles
        ├── cumulative_layout_shift
        │   ├── histogram
        │   └── percentiles
        ├── largest_contentful_paint
        │   ├── histogram
        │   └── percentiles
        ├── largest_contentful_paint_image_resource_load_delay
        │   └── percentiles
        ├── largest_contentful_paint_image_resource_load_duration
        │   └── percentiles
        ├── largest_contentful_paint_resource_type
        │   └── fractions
        ├── experimental_time_to_first_byte
        │   ├── histogram
        │   └── percentiles
        ├── first_contentful_paint
        │   ├── histogram
        │   └── percentiles
        ├── form_factors
        │   └── fractions
        ├── interaction_to_next_paint
        │   ├── histogram
        │   └── percentiles
        ├── largest_contentful_paint_image_element_render_delay
        │   └── percentiles
        └── largest_contentful_paint_image_time_to_first_byte
            └── percentiles
```

## Top-Level Fields

| Field | Type | Nullable | Description |
|------|------|----------|-------------|
| success | Boolean | No | Indicates whether the request completed successfully. |
| results | Object | No | Contains the Chrome UX Report response data. |

## Results Object

| Field | Type | Nullable | Description |
|------|------|----------|-------------|
| performance_ms | Integer | No | Server processing time in milliseconds. |
| url | String | No | URL analysed by the endpoint. |
| metrics | Object | No | Collection of Chrome UX Report metrics. |

## Metrics Object

| Field | Type | Nullable | Description |
|------|------|----------|-------------|
| round_trip_time | Object | No | Network round trip time distribution. |
| cumulative_layout_shift | Object | No | Layout stability distribution. |
| largest_contentful_paint | Object | No | Largest Contentful Paint distribution. |
| largest_contentful_paint_image_resource_load_delay | Object | No | Delay before loading the LCP image resource. |
| largest_contentful_paint_image_resource_load_duration | Object | No | Duration required to load the LCP image resource. |
| largest_contentful_paint_resource_type | Object | No | Distribution of LCP resource types. |
| experimental_time_to_first_byte | Object | No | Time to First Byte distribution. |
| first_contentful_paint | Object | No | First Contentful Paint distribution. |
| form_factors | Object | No | Device category distribution. |
| interaction_to_next_paint | Object | No | Interaction to Next Paint distribution. |
| largest_contentful_paint_image_element_render_delay | Object | No | Delay rendering the LCP image element. |
| largest_contentful_paint_image_time_to_first_byte | Object | No | Time from first byte to LCP image availability. |

## Histogram Object

Histogram objects describe the distribution of metric values across user experiences.

| Field | Type | Nullable | Description |
|------|------|----------|-------------|
| start | Integer/String | No | Lower bound of the histogram bucket. |
| end | Integer/String | Yes | Upper bound of the histogram bucket. |
| density | Number | No | Fraction of users represented by the bucket. |

## Percentiles Object

| Field | Type | Nullable | Description |
|------|------|----------|-------------|
| p75 | Integer/String | No | 75th percentile value for the metric. |

## Fractions Object

| Field | Type | Nullable | Description |
|------|------|----------|-------------|
| image | Number | Yes | Fraction of LCP resources that are images. |
| text | Number | Yes | Fraction of LCP resources that are text. |
| phone | Number | Yes | Fraction of users on mobile devices. |
| tablet | Number | Yes | Fraction of users on tablets. |
| desktop | Number | Yes | Fraction of users on desktop devices. |

## Data Types

The Enterprise SEO Metrics API uses the following JSON data types.

| Type | Description | Example |
|------|-------------|---------|
| String | UTF-8 encoded text | `"https://google.com"` |
| Integer | Whole number | `2405` |
| Number | Floating-point value | `0.757` |
| Boolean | Logical value | `true` |
| Object | JSON object | `{}` |
| Array | JSON list of values | `[]` |

## Nullable Fields

Some fields may be omitted depending on available Chrome UX Report data.

For example, image-specific Largest Contentful Paint metrics may not be returned when the analysed page does not contain a qualifying image element.

Applications should safely handle missing optional fields.

## Example Response

```json
{
  "success": true,
  "results": {
    "performance_ms": 113,
    "url": "https://google.com",
    "metrics": {
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
          }
        ],
        "percentiles": {
          "p75": 2405
        }
      },
      "cumulative_layout_shift": {
        "percentiles": {
          "p75": "0.00"
        }
      },
      "interaction_to_next_paint": {
        "percentiles": {
          "p75": 140
        }
      },
      "form_factors": {
        "fractions": {
          "phone": 0.1426,
          "tablet": 0,
          "desktop": 0.8574
        }
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

## Not Found Error (404)

Returned when Chrome UX Report data is unavailable for the requested URL.

### Schema

Uses the general error schema shown above.

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
    "code": 404,
    "status": "Not Found",
    "message": "No Chrome UX Report data found for the requested URL."
  }
}
```

## Server Error (500)

Returned when an unexpected server error occurs.

### Schema

Uses the general error schema shown above.

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
- Metric definitions are documented separately in `/definitions/crux.md`.
- Applications should ignore unknown fields to ensure forward compatibility with future API versions.