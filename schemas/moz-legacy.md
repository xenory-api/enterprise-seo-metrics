# Moz Legacy Response Schema

Comprehensive schema reference for the **Moz Legacy** endpoint.

This document describes the complete JSON response structure returned by the endpoint, including field names, data types, nullable values, and example payloads.

# Table of Contents

- [Overview](#overview)
- [Successful Response](#successful-response-200)
	- [Response Schema](#response-schema)
	- [Response Structure](#response-structure)
	- [Top-Level Fields](#top-level-fields)
	- [Results Object](#results-object)
	- [Metrics Object](#metrics-object)
	- [Data Types](#data-types)
	- [Nullable Fields](#nullable-fields)
	- [Example Response](#example-response)
- [Error Responses](#error-responses)
	- [Validation Error](#validation-error-422)
	- [Server Error](#server-error-500)
- [Notes](#notes)

# Overview

The **Moz Legacy** endpoint returns legacy SEO authority and backlink metrics sourced from Moz.

These metrics are maintained for backwards compatibility with applications that rely on Moz's legacy API and scoring methodology.

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
        "domain": {
          "type": "string"
        },
        "metrics": {
          "type": "object",
          "properties": {
            "moz_rank": {
              "type": "integer"
            },
            "page_rank": {
              "type": "number"
            },
            "spam_score": {
              "type": "integer"
            },
            "link_propensity": {
              "type": "integer"
            },
            "domain_authority": {
              "type": "integer"
            },
            "inbound_links": {
              "type": "integer"
            },
            "total_backlinks": {
              "type": "integer"
            },
            "broken_backlinks": {
              "type": "integer"
            },
            "referring_pages": {
              "type": "integer"
            },
            "referring_domains": {
              "type": "integer"
            },
            "referring_main_domains": {
              "type": "integer"
            },
            "linking_root_domains": {
              "type": "integer"
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
    ├── domain
    └── metrics
        ├── moz_rank
        ├── page_rank
        ├── spam_score
        ├── link_propensity
        ├── domain_authority
        ├── inbound_links
        ├── total_backlinks
        ├── broken_backlinks
        ├── referring_pages
        ├── referring_domains
        ├── referring_main_domains
        └── linking_root_domains
```

## Top-Level Fields

| Field | Type | Nullable | Description |
|------|------|----------|-------------|
| success | Boolean | No | Indicates whether the request completed successfully. |
| results | Object | No | Contains the response metadata and Moz Legacy metrics. |

## Results Object

| Field | Type | Nullable | Description |
|------|------|----------|-------------|
| performance_ms | Integer | No | Server processing time in milliseconds. |
| domain | String | No | Domain that was analysed. |
| metrics | Object | No | Collection of legacy Moz SEO metrics. |

## Metrics Object

| Field                  | Type    | Nullable | Description                                                         |
| -----------------------| ------- | -------- | ------------------------------------------------------------------- |
| moz_rank               | Integer | No       | Legacy MozRank score representing link popularity.                  |
| page_rank              | Number  | No       | Legacy Moz PageRank score.                                          |
| spam_score             | Integer | No       | Estimated likelihood that the domain exhibits spam characteristics. |
| link_propensity        | Integer | No       | Likelihood that pages on the domain link to external websites.      |
| domain_authority       | Integer | No       | Legacy Moz Domain Authority score.                                  |
| inbound_links          | Integer | No       | Total inbound links pointing to the analysed domain.                |
| total_backlinks        | Integer | No       | Total backlinks discovered in Moz's legacy index.                   |
| broken_backlinks       | Integer | No       | Backlinks pointing to inaccessible or broken pages.                 |
| referring_pages        | Integer | No       | Number of unique pages linking to the analysed domain.              |
| referring_domains      | Integer | No       | Number of unique domains linking to the analysed domain.            |
| referring_main_domains | Integer | No       | Number of unique main domains linking to the analysed domain.       |
| linking_root_domains   | Integer | No       | Number of unique root domains linking to the analysed domain.       |

## Data Types

The Enterprise SEO Metrics API uses the following JSON data types.

| Type | Description | Example |
|------|-------------|---------|
| String | UTF-8 encoded text | `"google.com"` |
| Integer | Whole number | `95` |
| Number | Floating-point value | `6.7` |
| Boolean | Logical value | `true` |
| Object | JSON object | `{}` |

## Nullable Fields

The Moz Legacy endpoint does not currently return nullable fields in successful responses.

Applications should still be designed to safely handle new optional fields that may be introduced in future API versions.

## Example Response

```json
{
  "success": true,
  "results": {
    "performance_ms": 189,
    "domain": "google.com",
    "metrics": {
      "moz_rank": 934,
      "page_rank": 9.99,
      "spam_score": 22,
      "link_propensity": 129,
      "domain_authority": 100,
      "inbound_links": 19444097169,
      "total_backlinks": 31208291664,
      "broken_backlinks": 667929049,
      "referring_pages": 25503478880,
      "referring_domains": 25912303,
      "referring_main_domains": 22429053,
      "linking_root_domains": 15785699
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

| Field | Type | Nullable | Description |
|------|------|----------|-------------|
| success | Boolean | No | Always `false`. |
| error | Object | No | Information describing the validation error. |

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
    "message": "The domain field is required."
  }
}
```

## Server Error (500)

Returned when an unexpected server error occurs.

### Schema

| Field | Type | Nullable | Description |
|------|------|----------|-------------|
| success | Boolean | No | Always `false`. |
| error | Object | No | Information describing the server error. |

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
- Metric definitions are documented separately in `/definitions/moz-legacy.md`.
- Applications should ignore unknown fields to ensure forward compatibility with future API versions.
