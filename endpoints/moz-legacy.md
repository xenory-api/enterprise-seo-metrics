# Moz Legacy Metrics API

Retrieve legacy Moz SEO metrics for a root domain, including historical authority scores, PageRank, backlink statistics, and legacy link metrics maintained for backwards compatibility.

## Overview

The **Moz Legacy Metrics API** provides access to Moz's legacy SEO metrics and link intelligence for a given root domain.

This endpoint is intended for applications that rely on historical Moz metric definitions or require backwards compatibility with older integrations.

Use this endpoint to retrieve:

- Domain Authority (Legacy)
- MozRank
- PageRank
- Spam Score
- Link Propensity
- Total backlinks
- Inbound links
- Referring pages and domains
- Linking root domains
- Broken backlink statistics

Common use cases include:

- Maintaining legacy SEO applications
- Historical trend analysis
- Migrating older Moz integrations
- Backwards-compatible reporting
- Domain authority comparison
- Legacy backlink analysis

# HTTP Request

`POST /moz-legacy`

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
| `domain` | string | Yes | Root domain to analyse (e.g. `google.com`) |

# Example Request

## cURL

```bash
curl --request POST \
  --url https://enterprise-seo-metrics.p.rapidapi.com/moz-legacy \
  --header "Content-Type: application/x-www-form-urlencoded" \
  --header "x-rapidapi-host: enterprise-seo-metrics.p.rapidapi.com" \
  --header "x-rapidapi-key: YOUR_API_KEY" \
  --data domain=google.com
```

# Successful Response

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

# Response Structure

## Top-Level Fields

| Field | Type | Description |
|-------|------|-------------|
| `success` | boolean | Indicates whether the request completed successfully |
| `results` | object | Legacy Moz metrics returned by the API |

## Results Object

| Field | Type | Description |
|-------|------|-------------|
| `performance_ms` | integer | API processing time in milliseconds |
| `domain` | string | Analysed root domain |
| `metrics` | object | Legacy Moz SEO metrics |

## Metrics Object

| Field | Type | Description |
|-------|------|-------------|
| `moz_rank` | integer | Legacy MozRank score |
| `page_rank` | number | Legacy Moz PageRank value |
| `spam_score` | integer | Legacy Moz Spam Score |
| `link_propensity` | integer | Legacy link propensity metric |
| `domain_authority` | integer | Legacy Moz Domain Authority score |
| `inbound_links` | integer | Total inbound links pointing to the analysed domain |
| `total_backlinks` | integer | Total backlinks discovered by Moz's legacy index |
| `broken_backlinks` | integer | Backlinks pointing to inaccessible or broken pages |
| `referring_pages` | integer | Unique pages linking to the analysed domain |
| `referring_domains` | integer | Unique domains linking to the analysed domain |
| `referring_main_domains` | integer | Unique main domains linking to the analysed domain |
| `linking_root_domains` | integer | Unique root domains linking to the analysed domain |

For detailed explanations of each metric, see:

```
/definitions/moz-legacy.md
```

# Status Codes

| Code | Description |
|------|-------------|
| `200 OK` | Metrics returned successfully |
| `422 Unprocessable Entity` | Invalid or missing domain |
| `500 Internal Server Error` | Unexpected server error |

# Error Responses

## Missing Parameter

```json
{
  "success": false,
  "error": {
    "code": 422,
    "status": "MISSING_PARAMETER",
    "message": "A valid root domain is required"
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

# Usage Notes

## Data Availability

- Metrics are sourced from Moz's legacy index.
- This endpoint is maintained primarily for backwards compatibility.
- Values may differ from those returned by the standard Moz Metrics endpoint.
- Historical coverage depends on Moz's available legacy dataset.

## Recommended Usage

This endpoint is well suited for:

- Legacy application support
- Historical SEO reporting
- Migration from older Moz APIs
- Comparing historical authority metrics
- Maintaining backwards compatibility with existing integrations

## Limitations

- Only root domains are supported.
- Invalid domains return a `422` response.
- Legacy metrics should not be directly compared with current Moz metrics without understanding differences in calculation methodology.

# Related Endpoints

- Moz Metrics
- Ahrefs Metrics
- Semrush Metrics
- Majestic Metrics

# Related Definitions

- Domain Authority
- MozRank
- PageRank
- Spam Score
- Link Propensity
- Linking Root Domains
