# Frequently Asked Questions

This guide answers common questions about the **Enterprise SEO Metrics API**, including authentication, subscriptions, requests, responses, and integration behaviour.

# Table of Contents

- [General Questions](#general-questions)
- [Authentication Questions](#authentication-questions)
- [Request Questions](#request-questions)
- [Response Questions](#response-questions)
- [Subscription Questions](#pricing-and-subscription-questions)
- [Troubleshooting Questions](#troubleshooting-questions)

# General Questions

## What is the Enterprise SEO Metrics API?

The Enterprise SEO Metrics API provides a unified REST interface for retrieving SEO, backlink, authority, website performance, and user experience metrics from multiple industry data providers.

The API allows developers to integrate SEO intelligence into:

- SEO platforms.
- Website auditing tools.
- Reporting dashboards.
- Marketing automation systems.
- Enterprise applications.

## Which data sources are supported?

The API currently provides access to:

- Moz Metrics.
- Moz Legacy Metrics.
- Ahrefs Metrics.
- Semrush Metrics.
- Majestic Metrics.
- Core Web Vitals.
- Chrome UX Report (CrUX).
- Anchor Text Analysis.
- Social Shares.

## Which HTTP methods does the API use?

All current API endpoints use HTTP `POST` requests. Each endpoint has its own URL path, request parameters, and response schema documented in:

```text
/endpoints
```

# Authentication Questions

## How do I authenticate requests?

The API uses RapidAPI authentication.

Every request requires:

- `X-RapidAPI-Key`
- `X-RapidAPI-Host`
- `Content-Type`

For complete authentication details, see:

```text
guides/authentication.md
```

## Can I use the same API key across multiple projects?

RapidAPI applications provide a single API key per application.

For separate projects, environments, or applications, it is recommended to create separate RapidAPI applications so usage analytics and credentials remain isolated.

## Can I expose my API key in frontend code?

No.

API keys should never be exposed in:

- Browser JavaScript.
- Mobile applications.
- Public repositories.
- Client-side applications.

Requests should be made from your backend or a secure server environment.

# Request Questions

## What URLs can I analyse?

The API accepts publicly accessible URLs.

Requests should include a complete and valid URL where required by the endpoint.

Example:

```text
https://example.com
```

## Do all endpoints require the same parameters?

No.

Each endpoint has its own request parameters and validation rules.

Refer to the endpoint documentation for the specific API you are using:

```text
/endpoints
```

## Can I send multiple URLs in a single request?

Currently, endpoints process one URL per request unless otherwise specified in the endpoint documentation. For analysing multiple URLs, applications should send separate requests while respecting their subscription limits.

# Response Questions

## Are all API responses formatted the same way?

Successful responses follow a consistent structure containing:

- `success`
- `results`
- Endpoint-specific metrics

However, the contents of `results` vary depending on the endpoint.

Complete response schemas are available in:

```text
/schemas
```

## Are response fields guaranteed to remain unchanged?

The API aims to maintain backwards compatibility. New fields may be added in future releases. Applications should ignore unknown fields to remain compatible with future API updates.

## Where can I find explanations of returned metrics?

Metric descriptions, data types, interpretations, and usage examples are available in:

```text
/definitions
```

# Pricing and Subscription Questions

## Is my payment information secure?

Credit card payments are processed through a PCI-compliant banking partner.

RapidAPI handles payment processing and subscription management securely.

## Why is a credit card required for a freemium API?

RapidAPI and API providers use subscription plans to provide transparent pricing and manage API usage. A credit card may be required even for free plans to support account verification and future plan upgrades. If you no longer wish to use the API, you can unsubscribe at any time through the Billing section of your RapidAPI Dashboard.

## What happens if I exceed my plan limits?

The Enterprise SEO Metrics API uses hard limits.

Once your plan quota has been reached, additional requests will not be processed until your quota resets or you upgrade your subscription.

For more information about quotas and limits, see:

```text
guides/rate-limits.md
```

## When will I be billed?

RapidAPI charges your payment method when you subscribe to an API plan and at each recurring billing interval, that is, on a monthly basis.

## How are refunds handled?

For refund requests, contact RapidAPI support:

```text
support@rapidapi.com
```

# Troubleshooting Questions

## Why am I receiving a 401 Unauthorized error?

A `401 Unauthorized` response usually means your API credentials are missing or invalid.

Check:

- Your `X-RapidAPI-Key`.
- Your `X-RapidAPI-Host`.
- Your subscription status.

See:

```text
guides/authentication.md
```

## Why am I receiving a 422 validation error?

A `422 Unprocessable Entity` response means the request was received but contains invalid or missing parameters. Common causes include:

- Missing `url` parameter.
- Invalid URL format.
- Incorrect parameter names.

Review the endpoint documentation for required parameters.

## Why am I receiving a 429 Too Many Requests error?

A `429` response means your application has exceeded its allowed request rate.

Recommended actions:

- Wait before retrying.
- Reduce request frequency.
- Review your remaining quota.

See:

```text
guides/rate-limits.md
```

## Why does the CrUX endpoint return 404?

The Chrome UX Report endpoint returns `404 Not Found` when no CrUX dataset exists for the requested URL.

This means the URL does not have available real-user Chrome UX data and is not necessarily an error with your request.

## Where can I report API issues?

When reporting an issue, include:

- The endpoint being called.
- The request timestamp.
- The complete error response.
- The RapidAPI request ID if available.

This information helps us diagnose problems more efficiently.