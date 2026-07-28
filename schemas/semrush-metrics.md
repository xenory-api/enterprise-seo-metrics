# Semrush Metrics Response Schema

Comprehensive schema reference for the **Semrush Metrics** endpoint.

This document describes the complete JSON response structure returned by the endpoint, including field names, data types, nullable values, and example payloads.

# Table of Contents

- [Overview](#overview)
- [Successful Response](#successful-response-200)
	- [Response Schema](#response-schema)
	- [Response Structure](#response-structure)
	- [Top-Level Fields](#top-level-fields)
	- [Results Object](#results-object)
	- [Data Object](#data-object)
	- [Metrics Object](#metrics-object)
		- [Score Metrics Object](#score-metrics-object)
		- [Backlink Audit Object](#backlink-audit-object)
	- [Distribution Object](#distribution-object)
		- [Organic Traffic Object](#organic-traffic-object)
		- [Referring Domains Object](#referring-domains-object)
	- [Data Types](#data-types)
	- [Nullable Fields](#nullable-fields)
	- [Example Response](#example-response)
- [Error Responses](#error-responses)
  - [Validation Error](#validation-error-422)
  - [Server Error](#server-error-500)
- [Notes](#notes)

# Overview

The **Semrush Metrics** endpoint returns SEO authority, backlink, organic traffic, and domain intelligence metrics sourced from Semrush.

The response includes overall domain metrics, backlink health indicators, backlink audit information, and traffic distribution data.

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
        "data": {
          "type": "object",
          "properties": {
            "metrics": {
              "type": "object",
              "properties": {
                "authority_score": {
                  "type": "integer"
                },
                "total_backlinks": {
                  "type": "integer"
                },
                "organic_traffic": {
                  "type": "integer"
                },
                "referring_domains": {
                  "type": "integer"
                },
                "score_metrics": {
                  "type": "object",
                  "properties": {
                    "link_power": {
                      "type": "number"
                    },
                    "search_traffic": {
                      "type": "number"
                    },
                    "naturalness": {
                      "type": "integer"
                    },
                    "health": {
                      "type": "integer"
                    },
                    "health_v2": {
                      "type": "integer"
                    },
                    "is_poor_links": {
                      "type": "boolean"
                    },
                    "is_poor_network": {
                      "type": "boolean"
                    },
                    "is_poor_ip_subnets": {
                      "type": "boolean"
                    },
                    "is_poor_refdomain_ip": {
                      "type": "boolean"
                    }
                  }
                },
                "backlink_audit": {
                  "type": "object",
                  "properties": {
                    "lost_backlinks": {
                      "type": "integer"
                    },
                    "new_backlinks": {
                      "type": "integer"
                    },
                    "new_referring_domains": {
                      "type": "integer"
                    },
                    "lost_referring_domains": {
                      "type": "integer"
                    },
                    "last_updated": {
                      "type": "string"
                    }
                  }
                }
              }
            },
            "distribution": {
              "type": "object",
              "properties": {
                "organic_traffic": {
                  "type": "object",
                  "properties": {
                    "aggregate": {
                      "type": "integer"
                    },
                    "databases": {
                      "type": "array",
                      "items": {
                        "type": "object"
                      }
                    }
                  }
                },
                "referring_domains": {
                  "type": "object",
                  "properties": {
                    "aggregate": {
                      "type": "integer"
                    },
                    "records": {
                      "type": "array",
                      "items": {
                        "type": "object",
                        "properties": {
                          "authority_score": {
                            "type": "integer"
                          },
                          "referring_domains": {
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
    └── data
        ├── metrics
        │   ├── authority_score
        │   ├── total_backlinks
        │   ├── organic_traffic
        │   ├── referring_domains
        │   ├── score_metrics
        │   │   ├── link_power
        │   │   ├── search_traffic
        │   │   ├── naturalness
        │   │   ├── health
        │   │   ├── health_v2
        │   │   ├── is_poor_links
        │   │   ├── is_poor_network
        │   │   ├── is_poor_ip_subnets
        │   │   └── is_poor_refdomain_ip
        │   └── backlink_audit
        │       ├── lost_backlinks
        │       ├── new_backlinks
        │       ├── new_referring_domains
        │       ├── lost_referring_domains
        │       └── last_updated
        └── distribution
            ├── organic_traffic
            │   ├── aggregate
            │   └── databases
            └── referring_domains
                ├── aggregate
                └── records
                    ├── authority_score
                    └── referring_domains
```

## Top-Level Fields

| Field | Type | Nullable | Description |
|------|------|----------|-------------|
| success | Boolean | No | Indicates whether the request completed successfully. |
| results | Object | No | Contains the Semrush metrics response data. |

## Results Object

| Field | Type | Nullable | Description |
|------|------|----------|-------------|
| performance_ms | Integer | No | Server processing time in milliseconds. |
| domain | String | No | Domain that was analysed. |
| data | Object | No | Contains Semrush metrics and distribution data. |

## Data Object

| Field | Type | Nullable | Description |
|------|------|----------|-------------|
| metrics | Object | No | Core Semrush SEO metrics. |
| distribution | Object | No | Geographic and category distribution data. |

## Metrics Object

| Field | Type | Nullable | Description |
|------|------|----------|-------------|
| authority_score | Integer | No | Semrush authority score for the domain. |
| total_backlinks | Integer | No | Total number of backlinks pointing to the domain. |
| organic_traffic | Integer | No | Estimated organic search traffic. |
| referring_domains | Integer | No | Number of referring domains pointing to the domain. |
| score_metrics | Object | No | Detailed backlink quality and health scoring metrics. |
| backlink_audit | Object | No | Backlink acquisition and loss tracking metrics. |

## Score Metrics Object

| Field | Type | Nullable | Description |
|------|------|----------|-------------|
| link_power | Number | No | Link strength metric. |
| search_traffic | Number | No | Search traffic contribution metric. |
| naturalness | Integer | No | Backlink profile naturalness score. |
| health | Integer | No | Backlink health score. |
| health_v2 | Integer | No | Updated backlink health score. |
| is_poor_links | Boolean | No | Indicates whether the backlink profile has poor link quality. |
| is_poor_network | Boolean | No | Indicates whether the domain has poor network characteristics. |
| is_poor_ip_subnets | Boolean | No | Indicates whether IP subnet diversity is considered poor. |
| is_poor_refdomain_ip | Boolean | No | Indicates whether referring domain IP diversity is considered poor. |

## Backlink Audit Object

| Field | Type | Nullable | Description |
|------|------|----------|-------------|
| lost_backlinks | Integer | No | Number of lost backlinks. |
| new_backlinks | Integer | No | Number of newly discovered backlinks. |
| new_referring_domains | Integer | No | Number of newly discovered referring domains. |
| lost_referring_domains | Integer | No | Number of lost referring domains. |
| last_updated | String | No | Timestamp indicating when the backlink audit data was updated. |

## Distribution Object

| Field | Type | Nullable | Description |
|------|------|----------|-------------|
| organic_traffic | Object | No | Organic traffic distribution data. |
| referring_domains | Object | No | Referring domain distribution data. |

## Organic Traffic Object

| Field | Type | Nullable | Description |
|------|------|----------|-------------|
| aggregate | Integer | No | Total aggregated organic traffic value. |
| databases | Array | No | Collection of database-specific traffic records. |

## Referring Domains Object

| Field | Type | Nullable | Description |
|------|------|----------|-------------|
| aggregate | Integer | No | Total aggregated referring domain count. |
| records | Array | No | Collection of referring domain distribution records. |

### Records Object

| Field | Type | Nullable | Description |
|------|------|----------|-------------|
| authority_score | Integer | No | Authority score associated with the record. |
| referring_domains | Integer | No | Number of referring domains represented by the record. |

## Data Types

The Enterprise SEO Metrics API uses the following JSON data types.

| Type | Description | Example |
|------|-------------|---------|
| String | UTF-8 encoded text | `"google.com"` |
| Integer | Whole number | `95000` |
| Number | Floating-point value | `87.5` |
| Boolean | Logical value | `true` |
| Object | JSON object | `{}` |
| Array | Ordered collection | `[]` |

## Nullable Fields

The Semrush Metrics endpoint does not currently return nullable fields in successful responses.

Applications should still be designed to safely handle new optional fields that may be introduced in future API versions.

## Example Response

```json
{
  "success": true,
  "results": {
    "performance_ms": 156,
    "domain": "google.com",
    "data": {
      "metrics": {
        "authority_score": 99,
        "total_backlinks": 3200000000,
        "organic_traffic": 850000000,
        "referring_domains": 4200000,
        "score_metrics": {
          "link_power": 98.5,
          "search_traffic": 97.2,
          "naturalness": 95,
          "health": 98,
          "health_v2": 97,
          "is_poor_links": false,
          "is_poor_network": false,
          "is_poor_ip_subnets": false,
          "is_poor_refdomain_ip": false
        },
        "backlink_audit": {
          "lost_backlinks": 12500,
          "new_backlinks": 42000,
          "new_referring_domains": 3500,
          "lost_referring_domains": 850,
          "last_updated": "2026-07-23T12:00:00Z"
        }
      },
      "distribution": {
        "organic_traffic": {
          "aggregate": 850000000,
          "databases": []
        },
        "referring_domains": {
          "aggregate": 4200000,
          "records": [
            {
              "authority_score": 90,
              "referring_domains": 250000
            }
          ]
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
    "message": "The domain field is required."
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
- Metric definitions are documented separately in `/definitions/semrush.md`.
- Applications should ignore unknown fields to ensure forward compatibility with future API versions.