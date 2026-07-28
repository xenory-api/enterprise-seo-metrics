# Ahrefs Metrics API

Retrieve comprehensive SEO metrics from Ahrefs, including Domain Rating, URL Rating, backlink data, referring domains, organic search performance, and paid search metrics.

## Overview

The **Ahrefs Metrics API** provides access to Ahrefs' extensive SEO dataset for domains, individual URLs, and subdomains.

Use this endpoint to retrieve:

- Domain Rating (DR)
- URL Rating (UR)
- Ahrefs Rank
- Domain Rank
- Backlink counts
- Referring domains
- Organic traffic estimates
- Organic traffic value
- Organic keyword counts
- Paid search traffic
- Paid keyword data

The endpoint supports multiple reporting modes, allowing you to retrieve metrics for an entire domain, a specific URL, or subdomains.

Common use cases include:

- SEO reporting dashboards
- Competitor analysis
- Backlink monitoring
- Domain authority assessment
- Organic traffic estimation
- Keyword opportunity research
- PPC competitor analysis

# HTTP Request

`POST /ahrefs-metrics`

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
| `url` | string | Yes | Domain or URL to analyse |
| `mode` | string | No | Dataset to retrieve. Defaults to `all`. |

### Available Modes

| Value | Description |
|-------|-------------|
| `all` | Returns all available metrics |
| `domain` | Domain-level metrics only |
| `exact_url` | URL-specific metrics only |
| `subdomains` | Aggregate subdomain metrics only |

# Example Request

## cURL

```bash
curl --request POST \
  --url https://enterprise-seo-metrics.p.rapidapi.com/ahrefs-metrics \
  --header "Content-Type: application/x-www-form-urlencoded" \
  --header "x-rapidapi-host: enterprise-seo-metrics.p.rapidapi.com" \
  --header "x-rapidapi-key: YOUR_API_KEY" \
  --data url=google.com \
  --data mode=all
```

# Successful Response

```json
{
  "success": true,
  "results": {
    "performance_ms": 213,
    "metrics": {
      "domain": {
        "domain_rating": 99,
        "ahrefs_rank": 3,
        "domain_rank": 3,
        "backlinks": 71189488347,
        "referring_domains": 34219158,
        "organic_traffic": 1322262400,
        "organic_cost": 25026940000,
        "organic_keywords": 71972747
      },
      "exact_url": {
        "url_rating": 68,
        "backlinks": 299756702,
        "referring_domains": 375368,
        "organic_traffic": 1469,
        "organic_cost": 13076,
        "organic_keywords": 221
      },
      "subdomains": {
        "live_backlinks": 2893220349,
        "all_time_backlinks": 876835992,
        "live_referring_domains": 17089024,
        "all_time_referring_domains": 1422279,
        "organic_traffic": 157553389,
        "organic_cost": 9570402321,
        "organic_keywords": 38191110,
        "organic_keywords_1_3": 10803366,
        "paid_traffic": 7321423,
        "paid_cost": 357113658,
        "paid_pages": 138095,
        "paid_keywords": 51050
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
| `results` | object | Ahrefs metrics returned by the API |

## Results Object

| Field | Type | Description |
|-------|------|-------------|
| `performance_ms` | integer | Total API processing time in milliseconds |
| `metrics` | object | Ahrefs SEO metrics |

## Domain Metrics

| Field | Type | Description |
|-------|------|-------------|
| `domain_rating` | integer | Ahrefs Domain Rating (DR) |
| `ahrefs_rank` | integer | Global Ahrefs Rank |
| `domain_rank` | integer | Domain ranking within Ahrefs |
| `backlinks` | integer | Total backlinks |
| `referring_domains` | integer | Total referring domains |
| `organic_traffic` | integer | Estimated monthly organic traffic |
| `organic_cost` | integer | Estimated monthly traffic value |
| `organic_keywords` | integer | Organic keywords ranking in search |

## Exact URL Metrics

| Field | Type | Description |
|-------|------|-------------|
| `url_rating` | integer | Ahrefs URL Rating (UR) |
| `backlinks` | integer | Backlinks to the analysed URL |
| `referring_domains` | integer | Referring domains to the URL |
| `organic_traffic` | integer | Estimated monthly organic traffic |
| `organic_cost` | integer | Estimated traffic value |
| `organic_keywords` | integer | Ranking organic keywords |

## Subdomain Metrics

| Field | Type | Description |
|-------|------|-------------|
| `live_backlinks` | integer | Current backlinks across subdomains |
| `all_time_backlinks` | integer | Historical backlink count |
| `live_referring_domains` | integer | Current referring domains |
| `all_time_referring_domains` | integer | Historical referring domains |
| `organic_traffic` | integer | Estimated monthly organic traffic |
| `organic_cost` | integer | Estimated monthly traffic value |
| `organic_keywords` | integer | Organic keywords |
| `organic_keywords_1_3` | integer | Keywords ranking in positions 1–3 |
| `paid_traffic` | integer | Estimated paid search traffic |
| `paid_cost` | integer | Estimated monthly advertising cost |
| `paid_pages` | integer | Pages receiving paid traffic |
| `paid_keywords` | integer | Paid search keywords |

For detailed explanations of each metric, see:

```
/definitions/ahrefs.md
```

# Status Codes

| Code | Description |
|------|-------------|
| `200 OK` | Metrics returned successfully |
| `422 Unprocessable Entity` | Missing or invalid parameters |
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

## Invalid Mode

```json
{
  "success": false,
  "error": {
    "code": 422,
    "status": "INVALID_PARAMETER",
    "message": "Invalid mode: <mode>",
    "details": {
      "default": "all",
      "allowed": "all,domain,exact_url,subdomains"
    }
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

## Error Object

| Field | Type | Description |
|-------|------|-------------|
| `code` | integer | HTTP status code |
| `status` | string | Machine-readable error identifier |
| `message` | string | Human-readable description |
| `details` | object | Additional validation information (when applicable) |

# Usage Notes

## Data Availability

- Metrics are sourced from Ahrefs' search index.
- Organic and paid search estimates are periodically refreshed.
- Historical backlink counts are available where supported by Ahrefs.

## Recommended Usage

This endpoint is ideal for:

- Domain authority analysis
- Backlink research
- Competitor benchmarking
- Organic visibility monitoring
- PPC intelligence
- SEO reporting
- Keyword opportunity analysis

## Limitations

- The `url` parameter must contain a valid domain or URL.
- Unsupported `mode` values return a `422` validation error.
- Some metrics may be unavailable for newly discovered websites.

# Related Endpoints

- Moz Metrics
- Moz Legacy Metrics
- Semrush Metrics
- Majestic Metrics

# Related Definitions

- Domain Rating
- URL Rating
- Ahrefs Rank
- Referring Domains
- Organic Traffic
- Organic Keywords
- Paid Traffic
- Paid Keywords
