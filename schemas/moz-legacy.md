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
            "spam_score": {
              "type": "integer"
            },
            "page_rank": {
              "type": "number"
            },
            "domain_authority": {
              "type": "integer"
            },
            "link_propensity": {
              "type": "integer"
            },
            "pages_to_subdomain": {
              "type": "integer"
            },
            "nofollow_pages_to_subdomain": {
              "type": "integer"
            },
            "redirect_pages_to_subdomain": {
              "type": "integer"
            },
            "external_pages_to_subdomain": {
              "type": "integer"
            },
            "external_nofollow_pages_to_subdomain": {
              "type": "integer"
            },
            "external_redirect_pages_to_subdomain": {
              "type": "integer"
            },
            "deleted_pages_to_subdomain": {
              "type": "integer"
            },
            "root_domains_to_subdomain": {
              "type": "integer"
            },
            "deleted_root_domains_to_subdomain": {
              "type": "integer"
            },
            "nofollow_root_domains_to_subdomain": {
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
        ├── spam_score
        ├── page_rank
        ├── domain_authority
        ├── link_propensity
        ├── pages_to_subdomain
        ├── nofollow_pages_to_subdomain
        ├── redirect_pages_to_subdomain
        ├── external_pages_to_subdomain
        ├── external_nofollow_pages_to_subdomain
        ├── external_redirect_pages_to_subdomain
        ├── deleted_pages_to_subdomain
        ├── root_domains_to_subdomain
        ├── deleted_root_domains_to_subdomain
        └── nofollow_root_domains_to_subdomain
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

| Field | Type | Nullable | Description |
|------|------|----------|-------------|
| spam_score | Integer | No | Estimated likelihood that the domain exhibits spam characteristics. |
| page_rank | Number | No | Legacy Moz PageRank score. |
| domain_authority | Integer | No | Legacy Moz Domain Authority score. |
| link_propensity | Integer | No | Likelihood that pages on the domain link to external websites. |
| pages_to_subdomain | Integer | No | Total pages associated with the analysed subdomain. |
| nofollow_pages_to_subdomain | Integer | No | Pages on the subdomain containing nofollow links. |
| redirect_pages_to_subdomain | Integer | No | Redirecting pages associated with the subdomain. |
| external_pages_to_subdomain | Integer | No | External pages linking to the subdomain. |
| external_nofollow_pages_to_subdomain | Integer | No | External pages providing nofollow backlinks to the subdomain. |
| external_redirect_pages_to_subdomain | Integer | No | External redirecting pages linking to the subdomain. |
| deleted_pages_to_subdomain | Integer | No | Deleted pages associated with the subdomain. |
| root_domains_to_subdomain | Integer | No | Unique root domains linking to the subdomain. |
| deleted_root_domains_to_subdomain | Integer | No | Deleted root domains previously linking to the subdomain. |
| nofollow_root_domains_to_subdomain | Integer | No | Root domains providing nofollow backlinks to the subdomain. |

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
    "performance_ms": 126,
    "domain": "google.com",
    "metrics": {
      "spam_score": 1,
      "page_rank": 6.8,
      "domain_authority": 95,
      "link_propensity": 89,
      "pages_to_subdomain": 27456321,
      "nofollow_pages_to_subdomain": 41789,
      "redirect_pages_to_subdomain": 3181,
      "external_pages_to_subdomain": 218943,
      "external_nofollow_pages_to_subdomain": 48216,
      "external_redirect_pages_to_subdomain": 7314,
      "deleted_pages_to_subdomain": 1824,
      "root_domains_to_subdomain": 6894123,
      "deleted_root_domains_to_subdomain": 47,
      "nofollow_root_domains_to_subdomain": 73542
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