# Social Shares Response Schema

Comprehensive schema reference for the **Social Shares** endpoint.

This document describes the complete JSON response structure returned by the endpoint, including field names, data types, nullable values, and example payloads.

# Table of Contents

- [Overview](#overview)
- [Successful Response](#successful-response-200)
	- [Response Schema](#response-schema)
	- [Response Structure](#response-structure)
	- [Top-Level Fields](#top-level-fields)
	- [Results Object](#results-object)
	- [Metrics Object](#metrics-object)
	- [Share Counts Object](#share-counts-object)
	- [Data Types](#data-types)
	- [Nullable Fields](#nullable-fields)
	- [Example Response](#example-response)
- [Error Responses](#error-responses)
	- [Validation Error](#validation-error-422)
  - [Server Error](#server-error-500)
- [Notes](#notes)

# Overview

The **Social Shares** endpoint returns social media engagement metrics for a requested URL.

Successful requests return share counts collected across supported social platforms, allowing applications to analyse content popularity and social engagement signals.

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
            "share_counts": {
              "type": "object",
              "properties": {
                "buffer": {
                  "type": "integer"
                },
                "facebook": {
                  "type": "integer"
                },
                "odnoklassniki": {
                  "type": "integer"
                },
                "pinterest": {
                  "type": "integer"
                },
                "tumblr": {
                  "type": "integer"
                },
                "vk": {
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
````

## Response Structure

```text
Response
├── success
└── results
    ├── performance_ms
    ├── url
    └── metrics
        └── share_counts
            ├── buffer
            ├── facebook
            ├── odnoklassniki
            ├── pinterest
            ├── tumblr
            └── vk
```

## Top-Level Fields

| Field   | Type    | Nullable | Description                                           |
| ------- | ------- | -------- | ----------------------------------------------------- |
| success | Boolean | No       | Indicates whether the request completed successfully. |
| results | Object  | No       | Contains the social share metrics.                    |

## Results Object

| Field          | Type    | Nullable | Description                              |
| -------------- | ------- | -------- | ---------------------------------------- |
| performance_ms | Integer | No       | Server processing time in milliseconds.  |
| url            | String  | No       | URL that was analysed.                   |
| metrics        | Object  | No       | Collection of social engagement metrics. |

## Metrics Object

| Field        | Type   | Nullable | Description                                         |
| ------------ | ------ | -------- | --------------------------------------------------- |
| share_counts | Object | No       | Social platform share counts for the requested URL. |

## Share Counts Object

| Field         | Type    | Nullable | Description                               |
| ------------- | ------- | -------- | ----------------------------------------- |
| buffer        | Integer | No       | Number of shares recorded through Buffer. |
| facebook      | Integer | No       | Number of Facebook shares.                |
| odnoklassniki | Integer | No       | Number of Odnoklassniki shares.           |
| pinterest     | Integer | No       | Number of Pinterest shares.               |
| tumblr        | Integer | No       | Number of Tumblr shares.                  |
| vk            | Integer | No       | Number of VK shares.                      |

## Data Types

The Enterprise SEO Metrics API uses the following JSON data types.

| Type    | Description          | Example         |
| ------- | -------------------- | --------------- |
| String  | UTF-8 encoded text   | `"google.com"` |
| Integer | Whole number         | `100`           |
| Number  | Floating-point value | `0.75`          |
| Boolean | Logical value        | `true`          |
| Object  | JSON object          | `{}`            |
| Array   | JSON array           | `[]`            |

## Nullable Fields

The Social Shares endpoint does not currently return nullable fields in successful responses.

Applications should still be designed to safely handle new optional fields that may be introduced in future API versions.

## Example Response

```json
{
  "success": true,
  "results": {
    "performance_ms": 92,
    "url": "https://google.com",
    "metrics": {
      "share_counts": {
        "buffer": 125,
        "facebook": 3420,
        "odnoklassniki": 56,
        "pinterest": 847,
        "tumblr": 93,
        "vk": 214
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

Returned when the request contains missing parameters.

### Schema

Uses the general error schema shown above.

### Error Object

| Field | Type | Nullable | Description |
|------|------|----------|-------------|
| code | Integer | No | HTTP status code. |
| status | String | No | Error status identifier. |
| message | String | No | Human-readable description of the validation error. |

### Example

```json
{
  "success": false,
  "error": {
    "code": 422,
    "status": "Unprocessable Entity",
    "message": "The URL field is required."
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
- Metric definitions are documented separately in `/definitions/social-shares.md`.
- Applications should ignore unknown fields to ensure forward compatibility with future API versions.