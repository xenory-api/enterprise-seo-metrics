# Moz Metrics Response Schema

Comprehensive schema reference for the **Moz Metrics** endpoint.

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

The **Moz Metrics** endpoint returns SEO authority, backlink, page, and domain metrics sourced from Moz.

Successful requests return a consistent JSON structure containing request metadata and a comprehensive collection of SEO metrics for the requested domain.

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
            "domain_authority": {
              "type": "integer"
            },
            "page_authority": {
              "type": "integer"
            },
            "spam_score": {
              "type": "integer"
            },
            "total_pages": {
              "type": "integer"
            },
            "deleted_pages": {
              "type": "integer"
            },
            "pages_crawled": {
              "type": "integer"
            },
            "external_pages": {
              "type": "integer"
            },
            "nofollow_pages": {
              "type": "integer"
            },
            "outbound_pages": {
              "type": "integer"
            },
            "redirect_pages": {
              "type": "integer"
            },
            "link_propensity": {
              "type": "number"
            },
            "outbound_domains": {
              "type": "integer"
            },
            "deleted_root_domains": {
              "type": "integer"
            },
            "root_domains_linking": {
              "type": "integer"
            },
            "indirect_root_domains": {
              "type": "integer"
            },
            "nofollow_root_domains": {
              "type": "integer"
            },
            "external_indirect_pages": {
              "type": "integer"
            },
            "external_nofollow_pages": {
              "type": "integer"
            },
            "external_redirect_pages": {
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
        ├── domain_authority
        ├── page_authority
        ├── spam_score
        ├── total_pages
        ├── deleted_pages
        ├── pages_crawled
        ├── external_pages
        ├── nofollow_pages
        ├── outbound_pages
        ├── redirect_pages
        ├── link_propensity
        ├── outbound_domains
        ├── deleted_root_domains
        ├── root_domains_linking
        ├── indirect_root_domains
        ├── nofollow_root_domains
        ├── external_indirect_pages
        ├── external_nofollow_pages
        └── external_redirect_pages
```

## Top-Level Fields

| Field | Type | Nullable | Description |
|------|------|----------|-------------|
| success | Boolean | No | Indicates whether the request completed successfully. |
| results | Object | No | Contains the response metadata and Moz metrics. |

## Results Object

| Field | Type | Nullable | Description |
|------|------|----------|-------------|
| performance_ms | Integer | No | Server processing time in milliseconds. |
| domain | String | No | Domain that was analysed. |
| metrics | Object | No | Collection of Moz SEO metrics. |

## Metrics Object

| Field | Type | Nullable | Description |
|------|------|----------|-------------|
| domain_authority | Integer | No | Moz Domain Authority score. |
| page_authority | Integer | No | Moz Page Authority score. |
| spam_score | Integer | No | Estimated likelihood that the domain exhibits spam characteristics. |
| total_pages | Integer | No | Total pages discovered for the domain. |
| deleted_pages | Integer | No | Number of deleted pages detected. |
| pages_crawled | Integer | No | Number of pages successfully crawled. |
| external_pages | Integer | No | Pages containing external links. |
| nofollow_pages | Integer | No | Pages containing nofollow links. |
| outbound_pages | Integer | No | Pages containing outbound links. |
| redirect_pages | Integer | No | Pages returning redirects. |
| link_propensity | Number | No | Likelihood that the website links to external websites. |
| outbound_domains | Integer | No | Number of unique outbound domains linked to. |
| deleted_root_domains | Integer | No | Root domains associated with deleted pages. |
| root_domains_linking | Integer | No | Unique root domains linking to the website. |
| indirect_root_domains | Integer | No | Root domains linking indirectly to the website. |
| nofollow_root_domains | Integer | No | Root domains providing nofollow backlinks. |
| external_indirect_pages | Integer | No | External pages linking indirectly to the website. |
| external_nofollow_pages | Integer | No | External pages containing nofollow backlinks. |
| external_redirect_pages | Integer | No | External pages linking through redirects. |

## Data Types

The Enterprise SEO Metrics API uses the following JSON data types.

| Type | Description | Example |
|------|-------------|---------|
| String | UTF-8 encoded text | `"google.com"` |
| Integer | Whole number | `95` |
| Number | Floating-point value | `0.823` |
| Boolean | Logical value | `true` |
| Object | JSON object | `{}` |

## Nullable Fields

The Moz Metrics endpoint does not currently return nullable fields in successful responses.

Applications should still be designed to safely handle new optional fields that may be introduced in future API versions.

## Example Response

```json
{
  "success": true,
  "results": {
    "performance_ms": 118,
    "domain": "google.com",
    "metrics": {
      "domain_authority": 95,
      "page_authority": 83,
      "spam_score": 1,
      "total_pages": 27456321,
      "deleted_pages": 1824,
      "pages_crawled": 27454497,
      "external_pages": 218943,
      "nofollow_pages": 41789,
      "outbound_pages": 197654,
      "redirect_pages": 3181,
      "link_propensity": 0.824,
      "outbound_domains": 16342,
      "deleted_root_domains": 47,
      "root_domains_linking": 6894123,
      "indirect_root_domains": 214985,
      "nofollow_root_domains": 73542,
      "external_indirect_pages": 193624,
      "external_nofollow_pages": 48216,
      "external_redirect_pages": 7314
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
- Metric definitions are documented separately in `/definitions/moz-metrics.md`.
- Applications should ignore unknown fields to ensure forward compatibility with future API versions.