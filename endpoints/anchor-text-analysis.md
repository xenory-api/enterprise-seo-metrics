# Anchor Text Analysis API

Retrieve comprehensive anchor text and backlink analysis data, including page-level anchor classifications, domain-level backlink distributions, and top backlink examples.

## Overview

The **Anchor Text Analysis API** provides detailed SEO analysis of anchor text usage across a webpage and its backlink profile.

Use this endpoint to retrieve:

- Page-level anchor tag analysis
- Internal and external link counts
- Anchor text classification distribution
- Domain-level backlink anchor distribution
- Backlink examples grouped by authority metrics
- Backlink examples grouped by domain rating

The endpoint analyses both on-page links and external backlink profiles to help understand anchor text patterns and link diversity.

Common use cases include:

- Anchor text auditing
- Backlink profile analysis
- Competitor SEO research
- Link building analysis
- Internal linking audits
- SEO reporting dashboards

# HTTP Request

`POST /anchor-text-analysis`

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

````

# Request Parameters

## Form Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `url` | string | Yes | Domain or URL to analyse |

# Example Request

## cURL

```bash
curl --request POST \
  --url https://enterprise-seo-metrics.p.rapidapi.com/anchor-text-analysis \
  --header "Content-Type: application/x-www-form-urlencoded" \
  --header "x-rapidapi-host: enterprise-seo-metrics.p.rapidapi.com" \
  --header "x-rapidapi-key: YOUR_API_KEY" \
  --data url=google.com
````

# Successful Response

```json
{
  "success": true,
  "results": {
    "performance_ms": 829,
    "url": "google.com",
    "data": {
      "page-level": {
        "url": "https://www.google.com/",
        "total_links": 10,
        "internal": 8,
        "external": 2
      },
      "domain-level": {
        "backlinks": {
          "aggregate": 7712067120
        }
      }
    }
  }
}
```

# Response Structure

## Top-Level Fields

| Field            | Type    | Description                                          |
| ---------------- | ------- | ---------------------------------------------------- |
| `success`        | boolean | Indicates whether the request completed successfully |
| `results`        | object  | Anchor text analysis response                        |
| `performance_ms` | integer | API processing time in milliseconds                  |
| `url`            | string  | Analysed URL                                         |
| `data`           | object  | Anchor text analysis data                            |

## Page-Level Analysis

The `page-level` object contains anchor information extracted directly from the analysed page.

| Field          | Type    | Description                      |
| -------------- | ------- | -------------------------------- |
| `url`          | string  | Analysed page URL                |
| `total_links`  | integer | Total number of links discovered |
| `internal`     | integer | Number of internal links         |
| `external`     | integer | Number of external links         |
| `distribution` | object  | Anchor type distribution         |
| `anchor_tags`  | array   | Individual anchor tag records    |

## Anchor Distribution

| Field         | Type    | Description              |
| ------------- | ------- | ------------------------ |
| `exact-match` | integer | Exact-match anchor count |
| `branded`     | integer | Branded anchor count     |
| `naked-url`   | integer | Naked URL anchor count   |
| `generic`     | integer | Generic anchor count     |
| `image`       | integer | Image anchor count       |
| `empty`       | integer | Empty anchor count       |

## Anchor Tag Object

| Field         | Type    | Description                        |
| ------------- | ------- | ---------------------------------- |
| `href`        | string  | Link destination URL               |
| `text`        | string  | Anchor text content                |
| `type`        | string  | Anchor classification type         |
| `is_internal` | boolean | Whether the link points internally |
| `is_nofollow` | boolean | Whether the link uses nofollow     |

## Domain-Level Analysis

The `domain-level` object contains backlink anchor analysis data.

| Field       | Type   | Description                               |
| ----------- | ------ | ----------------------------------------- |
| `backlinks` | object | Backlink anchor distribution and examples |

## Backlink Distribution

| Field          | Type    | Description              |
| -------------- | ------- | ------------------------ |
| `aggregate`    | integer | Total backlinks analysed |
| `distribution` | array   | Anchor type distribution |

## Anchor Type Distribution Object

| Field         | Type    | Description                                |
| ------------- | ------- | ------------------------------------------ |
| `anchor_type` | string  | Anchor classification                      |
| `backlinks`   | integer | Number of backlinks using this anchor type |
| `examples`    | array   | Example anchor text values                 |
| `percentage`  | object  | Percentage distribution                    |

## Percentage Object

| Field                 | Type    | Description             |
| --------------------- | ------- | ----------------------- |
| `value`               | number  | Raw percentage value    |
| `scaled`              | number  | Scaled percentage value |
| `scale_unit`          | string  | Percentage unit         |
| `scale_factor`        | integer | Scaling factor          |
| `significant_figures` | integer | Significant figures     |

Supported anchor classifications include:

- `branded`
- `partial-match`
- `exact-match`
- `generic`
- `other`
- `naked-url`
- `images`

## Top Backlinks by Authority Score

| Field             | Type    | Description                       |
| ----------------- | ------- | --------------------------------- |
| `authority_score` | integer | Authority score of referring page |
| `referring_text`  | string  | Text surrounding the backlink     |
| `referring_page`  | string  | Referring page URL                |
| `anchor_text`     | string  | Anchor text                       |
| `anchor_url`      | string  | Destination URL                   |
| `first_seen`      | string  | First discovery timestamp         |
| `last_seen`       | string  | Last discovery timestamp          |

## Top Backlinks by Domain Rating

| Field             | Type    | Description                  |
| ----------------- | ------- | ---------------------------- |
| `alt`             | string  | Alternative text             |
| `anchor`          | string  | Anchor text                  |
| `is_dofollow`     | boolean | Whether the link is dofollow |
| `domain_rating`   | integer | Referring domain rating      |
| `organic_traffic` | integer | Estimated organic traffic    |
| `link_type`       | string  | Link type                    |
| `link_context`    | string  | Surrounding link context     |
| `url_from`        | string  | Referring URL                |
| `url_to`          | string  | Destination URL              |
| `first_seen`      | string  | First discovery timestamp    |
| `last_seen`       | string  | Last discovery timestamp     |

For detailed explanations of each metric, see:

```
/definitions/anchor-text-analysis.md
```

# Status Codes

| Code                        | Description                           |
| --------------------------- | ------------------------------------- |
| `200 OK`                    | Anchor analysis returned successfully |
| `422 Unprocessable Entity`  | Missing or invalid parameters         |
| `500 Internal Server Error` | Unexpected server error               |

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

## Error Object

| Field     | Type    | Description                       |
| --------- | ------- | --------------------------------- |
| `code`    | integer | HTTP status code                  |
| `status`  | string  | Machine-readable error identifier |
| `message` | string  | Human-readable error description  |
| `details` | object  | Additional error information      |

# Usage Notes

## Data Availability

- Page-level data is generated from the analysed URL.
- Domain-level backlink data depends on indexed backlink coverage.
- Historical backlink timestamps are available when discovered.

## Recommended Usage

This endpoint is ideal for:

- Anchor text profile auditing
- Backlink quality analysis
- Internal linking reviews
- Competitor link analysis
- SEO reporting
- Link building research

## Limitations

- The `url` parameter must contain a valid domain or URL.
- Backlink data availability depends on indexed SEO datasets.
- Some backlink examples may be unavailable for smaller websites.

# Related Endpoints

- Moz Metrics
- Moz Legacy Metrics
- Ahrefs Metrics
- Semrush Metrics
- Majestic Metrics

# Related Definitions

- Anchor Text Types
- Backlink Metrics
- Domain Rating
- Authority Score
- Link Profile Analysis