# Majestic Metrics Response Schema

Comprehensive schema reference for the **Majestic Metrics** endpoint.

This document describes the complete JSON response structure returned by the endpoint, including field names, data types, nullable values, and example payloads.

# Table of Contents

- [Overview](#overview)
- [Successful Response](#successful-response-200)
	- [Response Schema](#response-schema)
	- [Response Structure](#response-structure)
	- [Top-Level Fields](#top-level-fields)
	- [Results Object](#results-object)
	- [Metrics Object](#metrics-object)
		- [Link Source Diversity Object](#link-source-diversity-object)
		- [External Inbound Links Object](#external-inbound-links-object)
		- [Referring Domains Object](#referring-domains-object)
		- [Nonunique Link Types Object](#nonunique-link-types-object)
		- [Total Nonunique Links Object](#total-nonunique-links-object)
		- [Outbound Link Context Object](#outbound-link-context-object)
	- [Data Types](#data-types)
	- [Nullable Fields](#nullable-fields)
	- [Example Response](#example-response)
- [Error Responses](#error-responses)
  - [Validation Error](#validation-error-422)
  - [Server Error](#server-error-500)
- [Notes](#notes)

# Overview

The **Majestic Metrics** endpoint returns link intelligence, authority, and backlink profile metrics sourced from Majestic.

The response includes authority scores, backlink counts, referring domain information, link source diversity metrics, link type distribution, and outbound link context.

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
            "ac_rank": {
              "type": "integer"
            },
            "trust_flow": {
              "type": "integer"
            },
            "trust_metric": {
              "type": "integer"
            },
            "citation_flow": {
              "type": "integer"
            },
            "indexed_urls": {
              "type": "integer"
            },
            "external_backlinks": {
              "type": "integer"
            },
            "referring_domains": {
              "type": "integer"
            },
            "link_source_diversity": {
              "type": "object",
              "properties": {
                "external_inbound_links": {
                  "type": "object",
                  "properties": {
                    "edu_backlinks": {
                      "type": "integer"
                    },
                    "edu_exact": {
                      "type": "integer"
                    },
                    "gov_backlinks": {
                      "type": "integer"
                    },
                    "gov_exact": {
                      "type": "integer"
                    }
                  }
                },
                "referring_domains": {
                  "type": "object",
                  "properties": {
                    "edu_domains": {
                      "type": "integer"
                    },
                    "edu_exact": {
                      "type": "integer"
                    },
                    "gov_domains": {
                      "type": "integer"
                    },
                    "gov_exact": {
                      "type": "integer"
                    }
                  }
                },
                "referring_ips": {
                  "type": "integer"
                },
                "referring_subnets": {
                  "type": "integer"
                }
              }
            },
            "nonunique_link_types": {
              "type": "object",
              "properties": {
                "homepages": {
                  "type": "integer"
                },
                "indirect": {
                  "type": "integer"
                },
                "deleted": {
                  "type": "integer"
                },
                "nofollow": {
                  "type": "integer"
                },
                "https": {
                  "type": "integer"
                },
                "frame": {
                  "type": "integer"
                },
                "image": {
                  "type": "integer"
                },
                "redirect": {
                  "type": "integer"
                },
                "text": {
                  "type": "integer"
                }
              }
            },
            "total_nonunique_links": {
              "type": "object",
              "properties": {
                "links": {
                  "type": "integer"
                },
                "types": {
                  "type": "integer"
                }
              }
            },
            "outbound_link_context": {
              "type": "object",
              "properties": {
                "internal_links": {
                  "type": "integer"
                },
                "external_links": {
                  "type": "integer"
                },
                "external_domains": {
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
        ├── ac_rank
        ├── trust_flow
        ├── trust_metric
        ├── citation_flow
        ├── indexed_urls
        ├── external_backlinks
        ├── referring_domains
        ├── link_source_diversity
        │   ├── external_inbound_links
        │   │   ├── edu_backlinks
        │   │   ├── edu_exact
        │   │   ├── gov_backlinks
        │   │   └── gov_exact
        │   ├── referring_domains
        │   │   ├── edu_domains
        │   │   ├── edu_exact
        │   │   ├── gov_domains
        │   │   └── gov_exact
        │   ├── referring_ips
        │   └── referring_subnets
        ├── nonunique_link_types
        │   ├── homepages
        │   ├── indirect
        │   ├── deleted
        │   ├── nofollow
        │   ├── https
        │   ├── frame
        │   ├── image
        │   ├── redirect
        │   └── text
        ├── total_nonunique_links
        │   ├── links
        │   └── types
        └── outbound_link_context
            ├── internal_links
            ├── external_links
            └── external_domains
```

## Top-Level Fields

| Field | Type | Nullable | Description |
|------|------|----------|-------------|
| success | Boolean | No | Indicates whether the request completed successfully. |
| results | Object | No | Contains the Majestic metrics response data. |

## Results Object

| Field | Type | Nullable | Description |
|------|------|----------|-------------|
| performance_ms | Integer | No | Server processing time in milliseconds. |
| url | String | No | URL analysed by the endpoint. |
| metrics | Object | No | Collection of Majestic SEO metrics. |

## Metrics Object

| Field | Type | Nullable | Description |
|------|------|----------|-------------|
| ac_rank | Integer | No | Majestic Alexa-style rank metric indicating link popularity. |
| trust_flow | Integer | No | Measures the quality of backlinks based on trusted sources. |
| trust_metric | Integer | No | Overall trust metric calculated from link quality signals. |
| citation_flow | Integer | No | Measures the influence based on the quantity of backlinks. |
| indexed_urls | Integer | No | Number of URLs indexed by Majestic. |
| external_backlinks | Integer | No | Total number of external backlinks. |
| referring_domains | Integer | No | Number of unique referring domains. |
| link_source_diversity | Object | No | Distribution of backlink source diversity. |
| nonunique_link_types | Object | No | Distribution of backlink types. |
| total_nonunique_links | Object | No | Total counts of nonunique links and link types. |
| outbound_link_context | Object | No | Information about outbound linking patterns. |

## Link Source Diversity Object

| Field | Type | Nullable | Description |
|------|------|----------|-------------|
| external_inbound_links | Object | No | Educational and governmental backlink counts. |
| referring_domains | Object | No | Educational and governmental referring domain counts. |
| referring_ips | Integer | No | Number of referring IP addresses. |
| referring_subnets | Integer | No | Number of referring IP subnets. |

## External Inbound Links Object

| Field | Type | Nullable | Description |
|------|------|----------|-------------|
| edu_backlinks | Integer | No | Number of backlinks from educational domains. |
| edu_exact | Integer | No | Exact educational domain backlink count. |
| gov_backlinks | Integer | No | Number of backlinks from government domains. |
| gov_exact | Integer | No | Exact government domain backlink count. |

## Referring Domains Object

| Field | Type | Nullable | Description |
|------|------|----------|-------------|
| edu_domains | Integer | No | Number of educational referring domains. |
| edu_exact | Integer | No | Exact educational referring domain count. |
| gov_domains | Integer | No | Number of government referring domains. |
| gov_exact | Integer | No | Exact government referring domain count. |

## Nonunique Link Types Object

| Field | Type | Nullable | Description |
|------|------|----------|-------------|
| homepages | Integer | No | Links originating from homepage URLs. |
| indirect | Integer | No | Indirect links. |
| deleted | Integer | No | Links from deleted pages. |
| nofollow | Integer | No | Nofollow links. |
| https | Integer | No | Links using HTTPS URLs. |
| frame | Integer | No | Links embedded through frames. |
| image | Integer | No | Image-based links. |
| redirect | Integer | No | Redirecting links. |
| text | Integer | No | Text-based links. |

## Total Nonunique Links Object

| Field | Type | Nullable | Description |
|------|------|----------|-------------|
| links | Integer | No | Total number of nonunique links. |
| types | Integer | No | Total number of link types detected. |

## Outbound Link Context Object

| Field | Type | Nullable | Description |
|------|------|----------|-------------|
| internal_links | Integer | No | Number of internal outbound links. |
| external_links | Integer | No | Number of external outbound links. |
| external_domains | Integer | No | Number of external domains linked to. |

## Data Types

The Enterprise SEO Metrics API uses the following JSON data types.

| Type | Description | Example |
|------|-------------|---------|
| String | UTF-8 encoded text | `"google.com"` |
| Integer | Whole number | `1000` |
| Boolean | Logical value | `true` |
| Object | JSON object | `{}` |

## Nullable Fields

The Majestic Metrics endpoint does not currently return nullable fields in successful responses.

Applications should still be designed to safely handle new optional fields that may be introduced in future API versions.

## Example Response

```json
{
  "success": true,
  "results": {
    "performance_ms": 134,
    "url": "google.com",
    "metrics": {
      "ac_rank": 1250,
      "trust_flow": 72,
      "trust_metric": 70,
      "citation_flow": 78,
      "indexed_urls": 250000,
      "external_backlinks": 5400000,
      "referring_domains": 85000,
      "link_source_diversity": {
        "external_inbound_links": {
          "edu_backlinks": 1200,
          "edu_exact": 950,
          "gov_backlinks": 800,
          "gov_exact": 600
        },
        "referring_domains": {
          "edu_domains": 350,
          "edu_exact": 280,
          "gov_domains": 220,
          "gov_exact": 180
        },
        "referring_ips": 62000,
        "referring_subnets": 41000
      },
      "nonunique_link_types": {
        "homepages": 500000,
        "indirect": 120000,
        "deleted": 45000,
        "nofollow": 700000,
        "https": 3000000,
        "frame": 1000,
        "image": 250000,
        "redirect": 30000,
        "text": 4900000
      },
      "total_nonunique_links": {
        "links": 5400000,
        "types": 9
      },
      "outbound_link_context": {
        "internal_links": 120000,
        "external_links": 25000,
        "external_domains": 3500
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
    "message": "The URL field is required."
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
- Metric definitions are documented separately in `/definitions/majestic.md`.
- Applications should ignore unknown fields to ensure forward compatibility with future API versions.