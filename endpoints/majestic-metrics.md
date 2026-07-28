# Majestic Metrics API

Retrieve Majestic SEO link intelligence including Trust Flow, Citation Flow, backlink statistics, referring domain analysis, and link profile diversity metrics.

## Overview

The **Majestic Metrics API** provides detailed backlink and link intelligence metrics for a domain or URL using Majestic's extensive link index.

Use this endpoint to retrieve:

- Trust Flow
- Citation Flow
- Trust Metric
- External backlinks
- Referring domains
- Indexed URL counts
- Educational link metrics
- Governmental link metrics
- Link type distribution
- Link source diversity
- Link context information

Common use cases include:

- Backlink profile analysis
- Domain authority evaluation
- Link quality assessment
- Competitor link research
- SEO reporting platforms
- Website auditing systems

This endpoint is designed for developers building:

- SEO platforms
- Website auditing tools
- Competitive analysis systems
- Reporting dashboards
- Marketing automation workflows

# HTTP Request

`POST /majestic-metrics`

# Authentication

This endpoint requires authentication using your RapidAPI subscription credentials.

Required headers:

| Header | Required | Description |
|---------|----------|-------------|
| `x-rapidapi-key` | Yes | Your RapidAPI API key |
| `x-rapidapi-host` | Yes | Enterprise SEO Metrics API host |
| `Content-Type` | Yes | `application/x-www-form-urlencoded` |

For authentication details, see:

```
guides/authentication.md
```

# Request Parameters

## Form Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `url` | string | Yes | Domain or URL to analyse (example: `google.com`) |

# Example Request

## cURL

```bash
curl --request POST \
  --url https://enterprise-seo-metrics.p.rapidapi.com/majestic-metrics \
  --header "Content-Type: application/x-www-form-urlencoded" \
  --header "x-rapidapi-host: enterprise-seo-metrics.p.rapidapi.com" \
  --header "x-rapidapi-key: YOUR_API_KEY" \
  --data url=google.com
```

# Successful Response

```json
{
  "success": true,
  "results": {
    "performance_ms": 138,
    "url": "google.com",
    "metrics": {
      "ac_rank": 0,
      "trust_flow": 100,
      "trust_metric": 100,
      "citation_flow": 99,
      "indexed_urls": 1968165429,
      "external_backlinks": 21890792348,
      "referring_domains": 26328259,
      "link_source_diversity": {
        "external_inbound_links": {
          "edu_backlinks": 450627956,
          "edu_exact": 31403437,
          "gov_backlinks": 89179697,
          "gov_exact": 19445936
        },
        "referring_domains": {
          "edu_domains": 68303,
          "edu_exact": 4320,
          "gov_domains": 227959,
          "gov_exact": 4108
        },
        "referring_ips": 2231045,
        "referring_subnets": 503589
      },
      "nonunique_link_types": {
        "homepages": 86178592,
        "indirect": 326972072,
        "deleted": 1089583386,
        "nofollow": 5259533640,
        "https": 22851849085,
        "frame": 2073979860,
        "image": 6492935928,
        "redirect": 150728436,
        "text": 17913560415
      },
      "total_nonunique_links": {
        "links": 26631204639,
        "types": 56245321414
      },
      "outbound_link_context": {
        "internal_links": 0,
        "external_links": 0,
        "external_domains": 0
      }
    }
  }
}
```

# Response Structure

## Top-Level Fields

| Field | Type | Description |
|-------|------|-------------|
| `success` | boolean | Indicates whether the request completed successfully |
| `results` | object | Majestic metrics response |

# Results Object

| Field | Type | Description |
|-------|------|-------------|
| `performance_ms` | integer | API processing time in milliseconds |
| `url` | string | Analysed domain or URL |
| `metrics` | object | Majestic SEO metrics |

# Core Metrics

| Field | Type | Description |
|-------|------|-------------|
| `ac_rank` | integer | Majestic Alexa-style ranking metric |
| `trust_flow` | integer | Trust Flow score based on backlink quality |
| `trust_metric` | integer | Trust Metric score |
| `citation_flow` | integer | Citation Flow score based on backlink quantity |
| `indexed_urls` | integer | Number of indexed URLs discovered |
| `external_backlinks` | integer | Total external backlinks |
| `referring_domains` | integer | Number of referring domains |

# Link Source Diversity

The `link_source_diversity` object provides information about the variety and quality of backlink sources.

## External Inbound Links

| Field | Type | Description |
|-------|------|-------------|
| `edu_backlinks` | integer | Backlinks from educational domains |
| `edu_exact` | integer | Exact educational domain backlinks |
| `gov_backlinks` | integer | Backlinks from government domains |
| `gov_exact` | integer | Exact government domain backlinks |

## Referring Domains

| Field | Type | Description |
|-------|------|-------------|
| `edu_domains` | integer | Educational referring domains |
| `edu_exact` | integer | Exact educational referring domains |
| `gov_domains` | integer | Government referring domains |
| `gov_exact` | integer | Exact government referring domains |

## Network Diversity

| Field | Type | Description |
|-------|------|-------------|
| `referring_ips` | integer | Number of referring IP addresses |
| `referring_subnets` | integer | Number of referring IP subnets |

# Non-Unique Link Types

The `nonunique_link_types` object provides backlink distribution by link type.

| Field | Type | Description |
|-------|------|-------------|
| `homepages` | integer | Homepage links |
| `indirect` | integer | Indirect links |
| `deleted` | integer | Deleted links |
| `nofollow` | integer | Nofollow links |
| `https` | integer | HTTPS links |
| `frame` | integer | Frame-based links |
| `image` | integer | Image links |
| `redirect` | integer | Redirect links |
| `text` | integer | Text links |

# Total Non-Unique Links

The `total_nonunique_links` object contains aggregate link counts.

| Field | Type | Description |
|-------|------|-------------|
| `links` | integer | Total non-unique links |
| `types` | integer | Total link types detected |

# Outbound Link Context

The `outbound_link_context` object provides outbound linking information.

| Field | Type | Description |
|-------|------|-------------|
| `internal_links` | integer | Internal outbound links |
| `external_links` | integer | External outbound links |
| `external_domains` | integer | External outbound domains |

For detailed explanations of each metric, see:

```
/definitions/majestic.md
```

# Status Codes

| Code | Description |
|------|-------------|
| `200 OK` | Metrics returned successfully |
| `422 Unprocessable Entity` | Missing or invalid URL |
| `500 Internal Server Error` | Unexpected server error |

# Error Responses

## Missing URL

```json
{
  "success": false,
  "error": {
    "code": 422,
    "status": "MISSING_PARAMETER",
    "message": "A valid URL is required"
  }
}
```

## Internal Server Error

```json
{
  "success": false,
  "error": {
    "code": 500,
    "status": "UNKNOWN_ERROR",
    "message": "The API threw a JavaScript exception."
  }
}
```

# Error Object

| Field | Type | Description |
|-------|------|-------------|
| `code` | integer | HTTP status code |
| `status` | string | Machine-readable error identifier |
| `message` | string | Human-readable error description |

# Usage Notes

## Data Availability

- Metrics are sourced from Majestic's backlink index.
- Trust Flow and Citation Flow are calculated from backlink relationships.
- Link metrics may change as Majestic refreshes its index.

## Recommended Usage

Recommended scenarios:

- Backlink quality scoring
- Link profile comparison
- Competitor research
- Domain authority analysis
- SEO audit workflows

## Limitations

- The `url` parameter must contain a valid domain or URL.
- Some outbound link context metrics may not be available for all domains.
- Link counts represent indexed backlink data and may differ between providers.

# Related Endpoints

- Moz Metrics
- Moz Legacy Metrics
- Ahrefs Metrics
- Semrush Metrics

# Related Definitions

- Trust Flow
- Citation Flow
- Trust Metric
- External Backlinks
- Referring Domains
- Link Source Diversity