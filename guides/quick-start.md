# Quick Start

This guide explains how to make your first request to the **Enterprise SEO Metrics API**.

By following these steps, you will:

1. Obtain API credentials.
2. Configure your request.
3. Send your first API call.
4. Parse the JSON response.

# Table of Contents

- [Overview](#overview)
- [Prerequisites](#prerequisites)
- [Step 1: Obtain an API Key](#step-1-obtain-an-api-key)
- [Step 2: Configure Your Request](#step-2-configure-your-request)
- [Step 3: Send Your First Request](#step-3-send-your-first-request)
- [Step 4: Understand the Response](#step-4-understand-the-response)
- [Next Steps](#next-steps)

# Overview

The Enterprise SEO Metrics API provides access to SEO, backlink, authority, performance, and website intelligence data through a unified REST API.

All API requests are made using HTTP `POST` requests and require RapidAPI authentication.

# Prerequisites

Before making requests, you need:

- A RapidAPI account.
- An active subscription to the Enterprise SEO Metrics API.
- Your RapidAPI API key.

For detailed authentication instructions, see:

```text
guides/authentication.md
```

# Step 1: Obtain an API Key

The Enterprise SEO Metrics API uses RapidAPI authentication. Your API key is provided through your RapidAPI application and must be included with every request.

Required header:

```http
X-RapidAPI-Key: YOUR_API_KEY
```

For more information about API keys and authentication headers, see:

```text
guides/authentication.md
```

# Step 2: Configure Your Request

Every request requires the following headers:

| Header            | Value                                   |
| ----------------- | --------------------------------------- |
| `X-RapidAPI-Key`  | Your RapidAPI API key                   |
| `X-RapidAPI-Host` | `enterprise-seo-metrics.p.rapidapi.com` |
| `Content-Type`    | `application/x-www-form-urlencoded`     |

Requests are sent to the following API host:

```text
https://enterprise-seo-metrics.p.rapidapi.com
```

Each endpoint has its own path and required parameters.

Available endpoints are documented in:

```text
/endpoints
```

# Step 3: Send Your First Request

The following example retrieves SEO metrics for a URL using the Social Shares endpoint.

## cURL

```bash
curl --request POST \
  --url https://enterprise-seo-metrics.p.rapidapi.com/social-shares \
  --header "Content-Type: application/x-www-form-urlencoded" \
  --header "x-rapidapi-host: enterprise-seo-metrics.p.rapidapi.com" \
  --header "x-rapidapi-key: YOUR_API_KEY" \
  --data url=https://google.com
```

Replace:

- `YOUR_API_KEY` with your RapidAPI API key.
- `https://google.com` with the URL you want to analyse.

# Step 4: Understand the Response

A successful request returns a JSON response containing:

- A success indicator.
- Request processing information.
- The requested metrics.

Example:

```json
{
  "success": true,
  "results": {
    "performance_ms": 133,
    "url": "https://google.com",
    "metrics": {
      "share_counts": {
        "facebook": 60243731,
        "buffer": 14813,
        "pinterest": 64,
        "tumblr": 1087,
        "vk": 303365,
        "odnoklassniki": 1298
      }
    }
  }
}
```

The exact response structure depends on the endpoint being called.

Complete response schemas are available in:

```text
/schemas
```

Detailed metric explanations are available in:

```text
/definitions
```

# Next Steps

After completing your first request:

- Review the available endpoints in `/endpoints`.
- Explore request examples in `/examples`.
- Review response structures in `/schemas`.
- Learn about authentication, errors, and quotas:

  - `guides/authentication.md`
  - `guides/error-handling.md`
  - `guides/rate-limits.md`

You are now ready to integrate the Enterprise SEO Metrics API into your application.