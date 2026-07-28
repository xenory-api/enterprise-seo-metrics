# Ahrefs Metrics Response Schema

Comprehensive schema reference for the **Ahrefs Metrics** endpoint.

This document describes the complete JSON response structure returned by the endpoint, including field names, data types, nullable values, and example payloads.

# Table of Contents

- [Overview](#overview)
- [Successful Response](#successful-response-200)
	- [Response Schema](#response-schema)
	- [Response Structure](#response-structure)
	- [Top-Level Fields](#top-level-fields)
	- [Results Object](#results-object)
	- [Metrics Object](#metrics-object)
		- [Domain Object](#domain-object)
		- [Exact URL Object](#exact-url-object)
		- [Subdomains Object](#subdomains-object)
	- [Data Types](#data-types)
	- [Nullable Fields](#nullable-fields)
	- [Example Response](#example-response)
- [Error Responses](#error-responses)
  - [Validation Error](#validation-error-422)
  - [Server Error](#server-error-500)
- [Notes](#notes)

# Overview

The **Ahrefs Metrics** endpoint returns SEO authority, backlink, keyword, and traffic metrics sourced from Ahrefs.

The response provides domain-level, exact URL-level, and subdomain-level metrics depending on the requested analysis mode.

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
        "metrics": {
          "type": "object",
          "properties": {
            "domain": {
              "type": "object",
              "properties": {
                "domain_rating": {
                  "type": "integer"
                },
                "ahrefs_rank": {
                  "type": "integer"
                },
                "domain_rank": {
                  "type": "integer"
                },
                "backlinks": {
                  "type": "integer"
                },
                "referring_domains": {
                  "type": "integer"
                },
                "organic_traffic": {
                  "type": "integer"
                },
                "organic_cost": {
                  "type": "integer"
                },
                "organic_keywords": {
                  "type": "integer"
                }
              }
            },
            "exact_url": {
              "type": "object",
              "properties": {
                "url_rating": {
                  "type": "integer"
                },
                "backlinks": {
                  "type": "integer"
                },
                "referring_domains": {
                  "type": "integer"
                },
                "organic_traffic": {
                  "type": "integer"
                },
                "organic_cost": {
                  "type": "integer"
                },
                "organic_keywords": {
                  "type": "integer"
                }
              }
            },
            "subdomains": {
              "type": "object",
              "properties": {
                "live_backlinks": {
                  "type": "integer"
                },
                "all_time_backlinks": {
                  "type": "integer"
                },
                "live_referring_domains": {
                  "type": "integer"
                },
                "all_time_referring_domains": {
                  "type": "integer"
                },
                "organic_traffic": {
                  "type": "integer"
                },
                "organic_cost": {
                  "type": "integer"
                },
                "organic_keywords": {
                  "type": "integer"
                },
                "organic_keywords_1_3": {
                  "type": "integer"
                },
                "paid_traffic": {
                  "type": "integer"
                },
                "paid_cost": {
                  "type": "integer"
                },
                "paid_pages": {
                  "type": "integer"
                },
                "paid_keywords": {
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
    └── metrics
        ├── domain
        │   ├── domain_rating
        │   ├── ahrefs_rank
        │   ├── domain_rank
        │   ├── backlinks
        │   ├── referring_domains
        │   ├── organic_traffic
        │   ├── organic_cost
        │   └── organic_keywords
        ├── exact_url
        │   ├── url_rating
        │   ├── backlinks
        │   ├── referring_domains
        │   ├── organic_traffic
        │   ├── organic_cost
        │   └── organic_keywords
        └── subdomains
            ├── live_backlinks
            ├── all_time_backlinks
            ├── live_referring_domains
            ├── all_time_referring_domains
            ├── organic_traffic
            ├── organic_cost
            ├── organic_keywords
            ├── organic_keywords_1_3
            ├── paid_traffic
            ├── paid_cost
            ├── paid_pages
            └── paid_keywords
```

## Top-Level Fields

| Field | Type | Nullable | Description |
|------|------|----------|-------------|
| success | Boolean | No | Indicates whether the request completed successfully. |
| results | Object | No | Contains the Ahrefs metrics response data. |

## Results Object

| Field | Type | Nullable | Description |
|------|------|----------|-------------|
| performance_ms | Integer | No | Server processing time in milliseconds. |
| metrics | Object | No | Collection of Ahrefs SEO metrics. |

## Metrics Object

The metrics object contains separate datasets for domain, exact URL, and subdomain analysis.

| Field | Type | Nullable | Description |
|------|------|----------|-------------|
| domain | Object | No | Domain-level SEO metrics. |
| exact_url | Object | No | Exact URL-level SEO metrics. |
| subdomains | Object | No | Subdomain-level SEO metrics. |

## Domain Object

| Field | Type | Nullable | Description |
|------|------|----------|-------------|
| domain_rating | Integer | No | Ahrefs Domain Rating score. |
| ahrefs_rank | Integer | No | Global Ahrefs rank based on backlink profile strength. |
| domain_rank | Integer | No | Domain ranking metric. |
| backlinks | Integer | No | Total backlinks pointing to the domain. |
| referring_domains | Integer | No | Number of unique referring domains. |
| organic_traffic | Integer | No | Estimated organic search traffic. |
| organic_cost | Integer | No | Estimated value of organic traffic. |
| organic_keywords | Integer | No | Number of keywords generating organic traffic. |

## Exact URL Object

| Field | Type | Nullable | Description |
|------|------|----------|-------------|
| url_rating | Integer | No | Ahrefs URL Rating score. |
| backlinks | Integer | No | Total backlinks pointing to the exact URL. |
| referring_domains | Integer | No | Number of referring domains pointing to the URL. |
| organic_traffic | Integer | No | Estimated organic traffic for the URL. |
| organic_cost | Integer | No | Estimated value of organic traffic for the URL. |
| organic_keywords | Integer | No | Number of organic ranking keywords for the URL. |

## Subdomains Object

| Field | Type | Nullable | Description |
|------|------|----------|-------------|
| live_backlinks | Integer | No | Number of currently active backlinks. |
| all_time_backlinks | Integer | No | Total backlinks discovered historically. |
| live_referring_domains | Integer | No | Active referring domains. |
| all_time_referring_domains | Integer | No | Historical referring domains. |
| organic_traffic | Integer | No | Estimated organic search traffic. |
| organic_cost | Integer | No | Estimated value of organic traffic. |
| organic_keywords | Integer | No | Total organic keywords. |
| organic_keywords_1_3 | Integer | No | Keywords ranking in positions 1–3. |
| paid_traffic | Integer | No | Estimated paid search traffic. |
| paid_cost | Integer | No | Estimated cost of paid search traffic. |
| paid_pages | Integer | No | Number of pages receiving paid search traffic. |
| paid_keywords | Integer | No | Number of paid search keywords. |

## Data Types

The Enterprise SEO Metrics API uses the following JSON data types.

| Type | Description | Example |
|------|-------------|---------|
| String | UTF-8 encoded text | `"google.com"` |
| Integer | Whole number | `95000` |
| Boolean | Logical value | `true` |
| Object | JSON object | `{}` |

## Nullable Fields

The Ahrefs Metrics endpoint does not currently return nullable fields in successful responses.

Applications should still be designed to safely handle new optional fields that may be introduced in future API versions.

## Example Response

```json
{
  "success": true,
  "results": {
    "performance_ms": 142,
    "metrics": {
      "domain": {
        "domain_rating": 99,
        "ahrefs_rank": 1,
        "domain_rank": 1,
        "backlinks": 1520000000,
        "referring_domains": 4200000,
        "organic_traffic": 900000000,
        "organic_cost": 850000000,
        "organic_keywords": 32000000
      },
      "exact_url": {
        "url_rating": 85,
        "backlinks": 250000,
        "referring_domains": 12000,
        "organic_traffic": 450000,
        "organic_cost": 380000,
        "organic_keywords": 15000
      },
      "subdomains": {
        "live_backlinks": 1200000,
        "all_time_backlinks": 2400000,
        "live_referring_domains": 35000,
        "all_time_referring_domains": 60000,
        "organic_traffic": 25000000,
        "organic_cost": 12000000,
        "organic_keywords": 500000,
        "organic_keywords_1_3": 45000,
        "paid_traffic": 100000,
        "paid_cost": 75000,
        "paid_pages": 2500,
        "paid_keywords": 8000
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

Returned when the request contains invalid parameters.

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
    "message": "Invalid mode parameter.",
    "details": {
      "default": "all",
      "allowed": "domain,url,subdomains"
    }
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
- Metric definitions are documented separately in `/definitions/ahrefs.md`.
- Ahrefs cost metrics are represented in USD cents.
- Applications should ignore unknown fields to ensure forward compatibility with future API versions.
