# Semrush Metrics API

Retrieve Semrush SEO intelligence including Authority Score, backlink metrics, organic search visibility, traffic distribution, and referring domain analysis for any root domain.

## Overview

The **Semrush Metrics API** provides comprehensive domain-level SEO metrics from Semrush data sources.

Use this endpoint to retrieve:

- Authority Score
- Total backlinks
- Referring domains
- Organic traffic estimates
- Organic traffic value
- Backlink quality scoring
- Backlink audit statistics
- Geographic traffic distribution
- Referring domain authority distribution

Common use cases include:

- SEO reporting platforms
- Competitor analysis tools
- Domain valuation systems
- Marketing intelligence dashboards
- Link profile monitoring
- Search visibility tracking

This endpoint is designed for developers building:

- SEO platforms
- Website auditing tools
- Competitive analysis systems
- Reporting dashboards
- Marketing automation workflows

# HTTP Request

`POST /semrush-metrics`

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
| `domain` | string | Yes | Root domain to analyse (example: `google.com`) |

# Example Request

## cURL

```bash
curl --request POST \
  --url https://enterprise-seo-metrics.p.rapidapi.com/semrush-metrics \
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
    "performance_ms": 1507,
    "domain": "google.com",
    "data": {
      "metrics": {
        "authority_score": 100,
        "total_backlinks": 45168718551,
        "organic_traffic": 4761203167,
        "referring_domains": 49761505
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
| `results` | object | Semrush metrics response |

# Results Object

| Field | Type | Description |
|-------|------|-------------|
| `performance_ms` | integer | API processing time in milliseconds |
| `domain` | string | Analysed root domain |
| `data` | object | Semrush metrics and distributions |

# Metrics Object

The `metrics` object contains high-level SEO performance indicators.

| Field | Type | Description |
|-------|------|-------------|
| `authority_score` | integer | Semrush Authority Score |
| `total_backlinks` | integer | Total backlinks pointing to the domain |
| `organic_traffic` | integer | Estimated organic search traffic |
| `referring_domains` | integer | Number of referring domains |

# Score Metrics Object

The `score_metrics` object provides detailed backlink quality indicators.

| Field | Type | Description |
|-------|------|-------------|
| `link_power` | number | Link authority score |
| `search_traffic` | number | Search traffic quality score |
| `naturalness` | number | Link profile naturalness score |
| `health` | number | Backlink health score |
| `health_v2` | number | Updated backlink health score |
| `is_poor_links` | boolean | Indicates poor link quality signals |
| `is_poor_network` | boolean | Indicates potentially poor network signals |
| `is_poor_ip_subnets` | boolean | Indicates suspicious IP subnet patterns |
| `is_poor_refdomain_ip` | boolean | Indicates suspicious referring domain IP patterns |

# Backlink Audit Object

The `backlink_audit` object provides recent backlink changes.

| Field | Type | Description |
|-------|------|-------------|
| `lost_backlinks` | integer | Recently lost backlinks |
| `new_backlinks` | integer | Newly discovered backlinks |
| `new_referring_domains` | integer | Newly discovered referring domains |
| `lost_referring_domains` | integer | Lost referring domains |
| `last_updated` | string | Timestamp of the latest backlink audit update |

# Distribution Data

The `distribution` object provides additional SEO analysis.

## Organic Traffic Distribution

The `organic_traffic` distribution contains traffic estimates grouped by country.

Structure:

| Field | Type | Description |
|-------|------|-------------|
| `aggregate` | integer | Total estimated organic traffic |
| `databases` | array | Country-level traffic records |

Country record:

| Field | Type | Description |
|-------|------|-------------|
| `alpha_2` | string | ISO country code |
| `country` | string/null | Country name |
| `traffic` | integer | Estimated organic traffic |

Example:

```json
{
  "alpha_2": "US",
  "country": "United States",
  "traffic": 555997415
}
```

## Referring Domain Distribution

The `referring_domains` distribution groups referring domains by Authority Score.

| Field | Type | Description |
|-------|------|-------------|
| `aggregate` | integer | Total referring domains analysed |
| `records` | array | Authority Score distribution |

Record structure:

| Field | Type | Description |
|-------|------|-------------|
| `authority_score` | integer | Semrush Authority Score bucket |
| `referring_domains` | integer | Number of domains in this bucket |

Example:

```json
{
  "authority_score": 90,
  "referring_domains": 31
}
```

For detailed explanations of each metric, see:

```
/definitions/semrush.md
```

# Status Codes

| Code | Description |
|------|-------------|
| `200 OK` | Metrics returned successfully |
| `422 Unprocessable Entity` | Missing or invalid domain |
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

# Usage Notes

## Data Availability

- Metrics are sourced from Semrush SEO datasets.
- Organic traffic values are estimated based on search visibility data.
- Backlink audit timestamps indicate the latest available refresh.

## Recommended Usage

Recommended scenarios:

- Domain authority monitoring
- Competitor SEO analysis
- Backlink quality evaluation
- International traffic analysis
- SEO reporting automation

## Limitations

- Only valid root domains are supported.
- Traffic values are estimates and may differ from first-party analytics.
- Distribution data availability depends on Semrush coverage.

# Related Endpoints

- Moz Metrics
- Moz Legacy Metrics
- Ahrefs Metrics
- Majestic Metrics

# Related Definitions

- Authority Score
- Backlink Audit
- Organic Traffic
- Referring Domains
- Traffic Distribution