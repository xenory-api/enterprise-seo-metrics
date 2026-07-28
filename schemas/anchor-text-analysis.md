# Anchor Text Analysis Response Schema

Comprehensive schema reference for the **Anchor Text Analysis** endpoint.

This document describes the complete JSON response structure returned by the endpoint, including field names, data types, nullable values, and example payloads.

# Table of Contents

- [Overview](#overview)
- [Successful Response](#successful-response-200)
	- [Response Schema](#response-schema)
	- [Response Structure](#response-structure)
	- [Top-Level Fields](#top-level-fields)
	- [Results Object](#results-object)
	- [Data Object](#data-object)
	- [Page-Level Object](#page-level-object)
	- [Distribution Object](#distribution-object)
	- [Anchor Tags Object](#anchor-tags-object)
	- [Domain-Level Object](#domain-level-object)
	- [Backlinks Object](#backlinks-object)
	- [Backlink Distribution Object](#backlink-distribution-object)
	- [Percentage Object](#percentage-object)
	- [Top Backlinks Object](#top-backlinks-object)
	- [Domain Rating Backlink Object](#domain-rating-backlink-object)
	- [Data Types](#data-types)
	- [Nullable Fields](#nullable-fields)
	- [Example Response](#example-response)
- [Error Responses](#error-responses)
  - [Validation Error](#validation-error-422)
  - [Server Error](#server-error-500)
- [Notes](#notes)

# Overview

The **Anchor Text Analysis** endpoint returns anchor text distribution and backlink anchor information for a requested URL.

Successful requests return page-level link analysis, anchor text categorisation, backlink distribution metrics, and detailed backlink examples.

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
        "data": {
          "type": "object",
          "properties": {
            "page-level": {
              "type": "object",
              "properties": {
                "url": {
                  "type": "string"
                },
                "total_links": {
                  "type": "integer"
                },
                "internal": {
                  "type": "integer"
                },
                "external": {
                  "type": "integer"
                },
                "distribution": {
                  "type": "object",
                  "properties": {
                    "exact-match": {
                      "type": "integer"
                    },
                    "branded": {
                      "type": "integer"
                    },
                    "naked-url": {
                      "type": "integer"
                    },
                    "generic": {
                      "type": "integer"
                    },
                    "image": {
                      "type": "integer"
                    },
                    "empty": {
                      "type": "integer"
                    }
                  }
                },
                "anchor_tags": {
                  "type": "array",
                  "items": {
                    "type": "object",
                    "properties": {
                      "href": {
                        "type": "string"
                      },
                      "text": {
                        "type": "string"
                      },
                      "type": {
                        "type": "string"
                      },
                      "is_internal": {
                        "type": "boolean"
                      },
                      "is_nofollow": {
                        "type": "boolean"
                      }
                    }
                  }
                }
              }
            },
            "domain-level": {
              "type": "object",
              "properties": {
                "backlinks": {
                  "type": "object",
                  "properties": {
                    "aggregate": {
                      "type": "integer"
                    },
                    "distribution": {
                      "type": "array",
                      "items": {
                        "type": "object",
                        "properties": {
                          "anchor_type": {
                            "type": "string"
                          },
                          "backlinks": {
                            "type": "integer"
                          },
                          "examples": {
                            "type": "array",
                            "items": {
                              "type": "string"
                            }
                          },
                          "percentage": {
                            "type": "object",
                            "properties": {
                              "value": {
                                "type": "number"
                              },
                              "scaled": {
                                "type": "number"
                              },
                              "scale_unit": {
                                "type": "string"
                              },
                              "scale_factor": {
                                "type": "integer"
                              },
                              "significant_figures": {
                                "type": "integer"
                              }
                            }
                          }
                        }
                      }
                    },
                    "top_backlinks": {
                      "type": "object",
                      "properties": {
                        "authority_score": {
                          "type": "array",
                          "items": {
                            "type": "object"
                          }
                        },
                        "domain_rating": {
                          "type": "array",
                          "items": {
                            "type": "object",
                            "properties": {
                              "alt": {
                                "type": "string"
                              },
                              "anchor": {
                                "type": "string"
                              },
                              "is_dofollow": {
                                "type": "boolean"
                              },
                              "domain_rating": {
                                "type": "integer"
                              },
                              "organic_traffic": {
                                "type": "integer"
                              },
                              "link_type": {
                                "type": "string"
                              },
                              "link_context": {
                                "type": "string"
                              },
                              "url_from": {
                                "type": "string"
                              },
                              "url_to": {
                                "type": "string"
                              },
                              "first_seen": {
                                "type": "string"
                              },
                              "last_seen": {
                                "type": "string"
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
    └── data
        ├── page-level
        │   ├── url
        │   ├── total_links
        │   ├── internal
        │   ├── external
        │   ├── distribution
        │   │   ├── exact-match
        │   │   ├── branded
        │   │   ├── naked-url
        │   │   ├── generic
        │   │   ├── image
        │   │   └── empty
        │   └── anchor_tags
        └── domain-level
            └── backlinks
                ├── aggregate
                ├── distribution
                └── top_backlinks
                    ├── authority_score
                    └── domain_rating
```

## Top-Level Fields

| Field   | Type    | Nullable | Description                                           |
| ------- | ------- | -------- | ----------------------------------------------------- |
| success | Boolean | No       | Indicates whether the request completed successfully. |
| results | Object  | No       | Contains the anchor text analysis results.            |

## Results Object

| Field          | Type    | Nullable | Description                                       |
| -------------- | ------- | -------- | ------------------------------------------------- |
| performance_ms | Integer | No       | Server processing time in milliseconds.           |
| url            | String  | No       | URL that was analysed.                            |
| data           | Object  | No       | Contains page-level and domain-level anchor data. |

## Data Object

| Field        | Type   | Nullable | Description                                 |
| ------------ | ------ | -------- | ------------------------------------------- |
| page-level   | Object | No       | Page-level anchor text analysis data.       |
| domain-level | Object | No       | Domain-level backlink anchor analysis data. |

## Page-Level Object

| Field        | Type    | Nullable | Description                              |
| ------------ | ------- | -------- | ---------------------------------------- |
| url          | String  | No       | Page URL analysed.                       |
| total_links  | Integer | No       | Total number of links found on the page. |
| internal     | Integer | No       | Number of internal links.                |
| external     | Integer | No       | Number of external links.                |
| distribution | Object  | No       | Distribution of anchor text categories.  |
| anchor_tags  | Array   | No       | List of analysed anchor tags.            |

## Distribution Object

| Field       | Type    | Nullable | Description                         |
| ----------- | ------- | -------- | ----------------------------------- |
| exact-match | Integer | No       | Number of exact-match anchor texts. |
| branded     | Integer | No       | Number of branded anchor texts.     |
| naked-url   | Integer | No       | Number of naked URL anchors.        |
| generic     | Integer | No       | Number of generic anchors.          |
| image       | Integer | No       | Number of image-based anchors.      |
| empty       | Integer | No       | Number of empty anchors.            |

## Anchor Tags Object

| Field       | Type    | Nullable | Description                             |
| ----------- | ------- | -------- | --------------------------------------- |
| href        | String  | No       | Link destination URL.                   |
| text        | String  | No       | Anchor text value.                      |
| type        | String  | No       | Anchor type classification.             |
| is_internal | Boolean | No       | Indicates whether the link is internal. |
| is_nofollow | Boolean | No       | Indicates whether the link is nofollow. |

## Domain-Level Object

| Field     | Type   | Nullable | Description                     |
| --------- | ------ | -------- | ------------------------------- |
| backlinks | Object | No       | Domain backlink anchor metrics. |

## Backlinks Object

| Field         | Type    | Nullable | Description                                |
| ------------- | ------- | -------- | ------------------------------------------ |
| aggregate     | Integer | No       | Total backlink count.                      |
| distribution  | Array   | No       | Backlink anchor type distribution.         |
| top_backlinks | Object  | No       | Top backlink records by authority metrics. |

## Backlink Distribution Object

| Field       | Type    | Nullable | Description                                |
| ----------- | ------- | -------- | ------------------------------------------ |
| anchor_type | String  | No       | Anchor text category.                      |
| backlinks   | Integer | No       | Number of backlinks using the anchor type. |
| examples    | Array   | No       | Example anchor texts.                      |
| percentage  | Object  | No       | Percentage breakdown of anchor usage.      |

## Percentage Object

| Field               | Type    | Nullable | Description                    |
| ------------------- | ------- | -------- | ------------------------------ |
| value               | Number  | No       | Percentage value.              |
| scaled              | Number  | No       | Scaled percentage value.       |
| scale_unit          | String  | No       | Unit used for scaling.         |
| scale_factor        | Integer | No       | Scaling factor.                |
| significant_figures | Integer | No       | Number of significant figures. |

## Top Backlinks Object

| Field           | Type  | Nullable | Description                          |
| --------------- | ----- | -------- | ------------------------------------ |
| authority_score | Array | No       | Backlinks ranked by authority score. |
| domain_rating   | Array | No       | Backlinks ranked by domain rating.   |

## Domain Rating Backlink Object

| Field           | Type    | Nullable | Description                                      |
| --------------- | ------- | -------- | ------------------------------------------------ |
| alt             | String  | No       | Alternative text associated with the backlink.   |
| anchor          | String  | No       | Anchor text.                                     |
| is_dofollow     | Boolean | No       | Indicates whether the backlink is dofollow.      |
| domain_rating   | Integer | No       | Rating of the linking domain.                    |
| organic_traffic | Integer | No       | Estimated organic traffic of the linking domain. |
| link_type       | String  | No       | Type of backlink.                                |
| link_context    | String  | No       | Context where the backlink appears.              |
| url_from        | String  | No       | Source URL containing the backlink.              |
| url_to          | String  | No       | Destination URL receiving the backlink.          |
| first_seen      | String  | No       | Date the backlink was first discovered.          |
| last_seen       | String  | No       | Date the backlink was last detected.             |

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

The Anchor Text Analysis endpoint does not currently return nullable fields in successful responses.

Applications should still be designed to safely handle new optional fields that may be introduced in future API versions.

## Example Response

```json
{
  "success": true,
  "results": {
    "performance_ms": 124,
    "url": "https://google.com",
    "data": {
      "page-level": {
        "url": "https://google.com",
        "total_links": 100,
        "internal": 75,
        "external": 25,
        "distribution": {
          "exact-match": 10,
          "branded": 30,
          "naked-url": 20,
          "generic": 15,
          "image": 5,
          "empty": 20
        },
        "anchor_tags": []
      },
      "domain-level": {
        "backlinks": {
          "aggregate": 10000,
          "distribution": [],
          "top_backlinks": {
            "authority_score": [],
            "domain_rating": []
          }
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
- Metric definitions are documented separately in `/definitions/anchor-text.md`.
- Applications should ignore unknown fields to ensure forward compatibility with future API versions.