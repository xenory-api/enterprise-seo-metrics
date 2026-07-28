# Social Shares API

Retrieve social media sharing metrics for a URL, including share counts across major social networks such as Facebook, Buffer, Pinterest, Tumblr, VK, and Odnoklassniki.

## Overview

The **Social Shares API** provides social engagement metrics for individual URLs by aggregating publicly available sharing activity across supported social platforms.

Use this endpoint to retrieve:

- Facebook share counts
- Buffer share counts
- Pinterest share counts
- Tumblr share counts
- VK share counts
- Odnoklassniki share counts

Common use cases include:

- Content performance analysis
- Social engagement reporting
- SEO content audits
- Competitor content research
- Link popularity analysis
- Digital marketing dashboards

# HTTP Request

`POST /social-shares`

# Authentication

This endpoint requires authentication using your RapidAPI subscription credentials.

Required headers:

| Header            | Required | Description                         |
| ----------------- | -------- | ----------------------------------- |
| `x-rapidapi-key`  | Yes      | Your RapidAPI API key               |
| `x-rapidapi-host` | Yes      | Enterprise SEO Metrics API host     |
| `Content-Type`    | Yes      | `application/x-www-form-urlencoded` |

For authentication details, see:

```
guides/authentication.md
```

# Request Parameters

## Form Parameters

| Parameter | Type   | Required | Description                              |
| --------- | ------ | -------- | ---------------------------------------- |
| `url`     | string | Yes      | URL to retrieve social share metrics for |

# Example Request

## cURL

```bash
curl --request POST \
  --url https://enterprise-seo-metrics.p.rapidapi.com/social-shares \
  --header "Content-Type: application/x-www-form-urlencoded" \
  --header "x-rapidapi-host: enterprise-seo-metrics.p.rapidapi.com" \
  --header "x-rapidapi-key: YOUR_API_KEY" \
  --data url=https://google.com
```

# Successful Response

```json
{
  "success": true,
  "results": {
    "performance_ms": 133,
    "url": "https://google.com",
    "metrics": {
      "share_counts": {
        "buffer": 14813,
        "facebook": 60243731,
        "odnoklassniki": 1298,
        "pinterest": 64,
        "tumblr": 1087,
        "vk": 303365
      }
    }
  }
}
```

# Response Structure

## Top-Level Fields

| Field     | Type    | Description                                          |
| --------- | ------- | ---------------------------------------------------- |
| `success` | boolean | Indicates whether the request completed successfully |
| `results` | object  | Social share metrics returned by the API             |

## Results Object

| Field            | Type    | Description                               |
| ---------------- | ------- | ----------------------------------------- |
| `performance_ms` | integer | Total API processing time in milliseconds |
| `url`            | string  | Analysed URL                              |
| `metrics`        | object  | Social engagement metrics                 |

## Metrics Object

| Field          | Type   | Description                 |
| -------------- | ------ | --------------------------- |
| `share_counts` | object | Social network share counts |

## Share Counts

| Field           | Type    | Description                    |
| --------------- | ------- | ------------------------------ |
| `facebook`      | integer | Number of Facebook shares      |
| `buffer`        | integer | Number of Buffer shares        |
| `pinterest`     | integer | Number of Pinterest shares     |
| `tumblr`        | integer | Number of Tumblr shares        |
| `vk`            | integer | Number of VK shares            |
| `odnoklassniki` | integer | Number of Odnoklassniki shares |

For detailed explanations of each metric, see:

```
/definitions/social-shares.md
```

# Status Codes

| Code                        | Description                                |
| --------------------------- | ------------------------------------------ |
| `200 OK`                    | Social share metrics returned successfully |
| `422 Unprocessable Entity`  | Missing or invalid parameters              |
| `500 Internal Server Error` | Unexpected server error                    |

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

| Field     | Type    | Description                                         |
| --------- | ------- | --------------------------------------------------- |
| `code`    | integer | HTTP status code                                    |
| `status`  | string  | Machine-readable error identifier                   |
| `message` | string  | Human-readable error description                    |
| `details` | object  | Additional validation information (when applicable) |

# Usage Notes

## Data Availability

- Social share counts represent aggregated engagement activity for the provided URL.
- Metrics availability depends on whether supported platforms expose share data.
- Counts may vary between platforms due to differences in indexing and update frequency.

## Recommended Usage

This endpoint is ideal for:

- Measuring content virality
- Comparing competitor content performance
- Building SEO and marketing reports
- Evaluating social distribution impact
- Identifying high-performing pages

## Limitations

- The `url` parameter must contain a valid URL.
- Social platforms may update or restrict publicly available share data.
- Some platforms may return limited or unavailable metrics depending on URL popularity and indexing.

# Related Endpoints

- Anchor Text Analysis
- Backlink Metrics
- Ahrefs Metrics
- Semrush Metrics
- Majestic Metrics
- Core Web Vitals

# Related Definitions

- Social Shares
- Facebook Shares
- Pinterest Shares
- Social Engagement
- Content Popularity
- Link Popularity