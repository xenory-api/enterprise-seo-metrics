# Rate Limits

This guide explains how request quotas and rate limits are enforced by the **Enterprise SEO Metrics API**, how to monitor your remaining allowance, and how to handle rate limit responses. Understanding these limits helps you build reliable integrations and avoid unnecessary request failures.

# Table of Contents

- [Overview](#overview)
- [Subscription Plans](#subscription-plans)
- [Rate Limit Headers](#rate-limit-headers)
- [Too Many Requests](#http-429-too-many-requests)
- [Handling Rate Limits](#handling-rate-limits)

# Overview

The Enterprise SEO Metrics API is distributed through RapidAPI.

Every subscription plan includes:

- A monthly request quota (hard limit)
- A maximum request rate (requests per minute)

Once your monthly quota has been exhausted, additional requests cannot be processed until your quota resets or your subscription is upgraded.

If your application exceeds the permitted request rate, RapidAPI temporarily rejects additional requests with a `429 Too Many Requests` response.

# Subscription Plans

The Enterprise SEO Metrics API currently offers the following subscription plans.

| Plan        | Monthly Requests |              Rate Limit |
| ----------- | ---------------: | ----------------------: |
| **Basic**   |               25 |   5 requests per minute |
| **Pro**     |            5,000 |  60 requests per minute |
| **Ultra** ⭐ |           25,000 | 120 requests per minute |
| **Mega**    |          100,000 | 300 requests per minute |

> **Note:** Subscription plans, pricing, and request limits may change over time. Always refer to the RapidAPI marketplace listing for the latest limits available to your account.

# Rate Limit Headers

Every successful response includes headers that describe your current request quota.

Example:

```http
x-ratelimit-rapid-free-plans-hard-limit-limit: 500000
x-ratelimit-rapid-free-plans-hard-limit-remaining: 482007
x-ratelimit-rapid-free-plans-hard-limit-reset: 1169083

x-ratelimit-requests-limit: 500000
x-ratelimit-requests-remaining: 482007
x-ratelimit-requests-reset: 1169083
```

The most useful headers are:

| Header                           | Description                                                 |
| -------------------------------- | ----------------------------------------------------------- |
| `x-ratelimit-requests-limit`     | Total requests available during the current quota period.   |
| `x-ratelimit-requests-remaining` | Number of requests remaining before the quota is exhausted. |
| `x-ratelimit-requests-reset`     | Time remaining until the current request quota resets.      |

Additional RapidAPI response headers may also be returned.

| Header                  | Description                                                        |
| ----------------------- | ------------------------------------------------------------------ |
| `x-rapidapi-region`     | RapidAPI gateway region that processed the request.                |
| `x-rapidapi-request-id` | Unique identifier for the request, useful when contacting support. |
| `x-rapidapi-version`    | RapidAPI gateway version that processed the request.               |

Applications can use the rate limit headers to monitor usage and proactively avoid exceeding their available quota.

# HTTP 429 Too Many Requests

If your application exceeds the permitted request rate, RapidAPI returns:

```http
HTTP/1.1 429 Too Many Requests
```

Example response:

```json
{
  "success": false,
  "error": {
    "code": 429,
    "status": "Too Many Requests",
    "message": "Rate limit exceeded. Please try again later."
  }
}
```

Thus indicating that your application has temporarily exceeded the allowed request rate.

This does **not** indicate:

- An authentication failure.
- An invalid request.
- A server-side error.

Instead, it means your application should reduce the rate at which it sends requests.

# Handling Rate Limits

If your application receives a `429 Too Many Requests` response:

1. Stop sending additional requests temporarily.
2. Wait before retrying the request.
3. Increase the delay if additional `429` responses are received.
4. Resume requests at a lower rate.

Applications that perform automated or high-volume processing should implement exponential backoff when retrying rate-limited requests.