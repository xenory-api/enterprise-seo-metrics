# Moz Legacy Metrics API

Retrieve legacy Moz SEO metrics for a root domain, including historical authority scores, PageRank, backlink statistics, and subdomain link metrics maintained for backwards compatibility.

## Overview

The **Moz Legacy Metrics API** provides access to Moz's legacy SEO metrics and link intelligence for a given root domain.

This endpoint is intended for applications that rely on historical Moz metric definitions or require backwards compatibility with older integrations.

Use this endpoint to retrieve:

- Domain Authority (Legacy)
- PageRank
- Spam Score
- Link Propensity
- Root domains linking to the subdomain
- External backlink statistics
- Redirect and nofollow link metrics
- Historical page counts

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
    "performance_ms": 1011,
    "domain": "google.com",
    "metrics": {
      "spam_score": 22,
      "page_rank": 9.99,
      "domain_authority": 100,
      "link_propensity": 129,
      "pages_to_subdomain": 19444097169,
      "nofollow_pages_to_subdomain": 3085674502,
      "redirect_pages_to_subdomain": 776128160,
      "external_pages_to_subdomain": 19224336868,
      "external_nofollow_pages_to_subdomain": 3085674498,
      "external_redirect_pages_to_subdomain": 775513421,
      "deleted_pages_to_subdomain": 2636646206,
      "root_domains_to_subdomain": 15785699,
      "deleted_root_domains_to_subdomain": 1503770,
      "nofollow_root_domains_to_subdomain": 1153531
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
| `performance_ms` | integer | Total API processing time in milliseconds |
| `domain` | string | Analysed root domain |
| `metrics` | object | Legacy Moz SEO metrics |

## Metrics Object

| Field | Type | Description |
|-------|------|-------------|
| `spam_score` | integer | Legacy Moz Spam Score |
| `page_rank` | number | Legacy Moz PageRank value |
| `domain_authority` | integer | Legacy Moz Domain Authority score |
| `link_propensity` | integer | Legacy link propensity metric |
| `pages_to_subdomain` | integer | Total pages linking to the analysed subdomain |
| `nofollow_pages_to_subdomain` | integer | Nofollow pages linking to the subdomain |
| `redirect_pages_to_subdomain` | integer | Redirect pages linking to the subdomain |
| `external_pages_to_subdomain` | integer | External pages linking to the subdomain |
| `external_nofollow_pages_to_subdomain` | integer | External nofollow pages linking to the subdomain |
| `external_redirect_pages_to_subdomain` | integer | External redirect pages linking to the subdomain |
| `deleted_pages_to_subdomain` | integer | Deleted pages previously linking to the subdomain |
| `root_domains_to_subdomain` | integer | Unique root domains linking to the subdomain |
| `deleted_root_domains_to_subdomain` | integer | Deleted root domains previously linking to the subdomain |
| `nofollow_root_domains_to_subdomain` | integer | Root domains providing only nofollow links |

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
- PageRank
- Spam Score
- Root Domains to Subdomain
- Link Propensity