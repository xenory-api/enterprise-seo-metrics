# Moz Metrics API

Retrieve authoritative SEO metrics, backlink intelligence, and domain authority data for any root domain using Moz's industry-leading SEO index.

## Overview

The **Moz Metrics API** provides comprehensive SEO authority and backlink metrics for a given root domain.

Use this endpoint to retrieve:

- Domain Authority (DA)
- Page Authority (PA)
- Spam Score
- Root domains linking
- Indexed page counts
- Redirect statistics
- Nofollow link metrics
- Outbound link metrics
- Link propensity indicators

Common use cases include:

- Website authority analysis
- SEO reporting dashboards
- Competitor research
- Domain quality assessment
- Link profile monitoring
- Marketing automation
- Technical SEO auditing

# HTTP Request

`POST /moz-metrics`

# Authentication

This endpoint requires authentication using your RapidAPI subscription credentials.

Required headers:

| Header | Required | Description |
|---------|----------|-------------|
| `x-rapidapi-key` | Yes | Your RapidAPI API key |
| `x-rapidapi-host` | Yes | Enterprise SEO Metrics API host |
| `Content-Type` | Yes | `application/x-www-form-urlencoded` |

For authentication details, see:

- `guides/authentication.md`

# Request Parameters

## Form Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `domain` | string | Yes | Root domain to analyse (e.g. `google.com`) |

# Example Request

## cURL

```bash
curl --request POST \
  --url https://enterprise-seo-metrics.p.rapidapi.com/moz-metrics \
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
    "performance_ms": 59,
    "domain": "google.com",
    "metrics": {
      "domain_authority": 94,
      "page_authority": 91,
      "spam_score": 1,
      "total_pages": 1601251461,
      "deleted_pages": 164168712,
      "pages_crawled": 17104973,
      "external_pages": 1601237259,
      "nofollow_pages": 130780890,
      "outbound_pages": 4977777,
      "redirect_pages": 361022707,
      "link_propensity": 0.000010230943,
      "outbound_domains": 175,
      "deleted_root_domains": 185266,
      "root_domains_linking": 1312893,
      "indirect_root_domains": 351671,
      "nofollow_root_domains": 210370,
      "external_indirect_pages": 216149555,
      "external_nofollow_pages": 130780890,
      "external_redirect_pages": 361008517
    }
  }
}
```

# Response Structure

## Top-Level Fields

| Field | Type | Description |
|-------|------|-------------|
| `success` | boolean | Indicates whether the request completed successfully |
| `results` | object | SEO metrics returned by the API |

## Results Object

| Field | Type | Description |
|-------|------|-------------|
| `performance_ms` | integer | Total API processing time in milliseconds |
| `domain` | string | Analysed root domain |
| `metrics` | object | Moz SEO metrics |

## Metrics Object

| Field | Type | Description |
|-------|------|-------------|
| `domain_authority` | integer | Moz Domain Authority score |
| `page_authority` | integer | Moz Page Authority score |
| `spam_score` | integer | Estimated spam score |
| `total_pages` | integer | Total indexed pages |
| `deleted_pages` | integer | Deleted pages detected |
| `pages_crawled` | integer | Pages successfully crawled |
| `external_pages` | integer | Pages containing external links |
| `nofollow_pages` | integer | Pages containing nofollow links |
| `outbound_pages` | integer | Pages containing outbound links |
| `redirect_pages` | integer | Redirecting pages |
| `link_propensity` | number | Estimated probability of outbound linking |
| `outbound_domains` | integer | Unique outbound domains |
| `deleted_root_domains` | integer | Deleted linking root domains |
| `root_domains_linking` | integer | Linking root domains |
| `indirect_root_domains` | integer | Indirect linking root domains |
| `nofollow_root_domains` | integer | Root domains providing nofollow links |
| `external_indirect_pages` | integer | External indirect linking pages |
| `external_nofollow_pages` | integer | External nofollow pages |
| `external_redirect_pages` | integer | External redirect pages |

For detailed explanations of each metric, see:

```
/definitions/moz.md
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

- Metrics are sourced from Moz's proprietary search index.
- Values may change as Moz refreshes its index.
- Newly registered domains may have limited or unavailable data.

## Recommended Usage

This endpoint is well suited for:

- Authority scoring
- Domain comparisons
- SEO reporting
- Competitor analysis
- Link profile monitoring

## Limitations

- Only root domains are supported.
- Invalid domains return a `422` response.
- Results depend on Moz's available crawl data.

# Related Endpoints

- Moz Legacy Metrics
- Ahrefs Metrics
- Semrush Metrics
- Majestic Metrics

# Related Definitions

- Domain Authority
- Page Authority
- Spam Score
- Root Domains Linking
- Link Propensity