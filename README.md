# Enterprise SEO Metrics API Documentation

Comprehensive developer documentation for the **Enterprise SEO Metrics API**.

The Enterprise SEO Metrics API provides a unified REST interface for retrieving SEO, backlink, authority, website performance, and user experience metrics from leading industry data providers. It enables developers, SaaS platforms, SEO professionals, digital agencies, and enterprise applications to integrate reliable website intelligence through a single API.

Whether you're building an SEO platform, website auditing solution, competitor analysis tool, reporting dashboard, or marketing automation workflow, this documentation provides everything required to integrate the API efficiently.

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Supported APIs](#supported-apis)
- [Repository Structure](#repository-structure)
- [Quick Start](#quick-start)
- [Authentication](#authentication)
- [API Endpoints](#api-endpoints)
- [Response Schemas](#response-schemas)
- [Code Examples](#code-examples)
- [Data Dictionary](#metric-definitions)
- [Guides](#guides)
    - [Rate Limits](#rate-limits)
    - [Error Handling](#error-handling)
    - [Versioning](#versioning)
- [Contributing](#contributing)
- [Support](#support)

# Overview

The Enterprise SEO Metrics API consolidates SEO and website intelligence into a single REST API.

Instead of integrating multiple third-party providers independently, developers can access comprehensive website metrics through consistent endpoints, authentication, and response formats.

Available data includes:

- Website authority metrics
- Backlink intelligence
- Domain popularity
- Link profile analysis
- Core Web Vitals
- Chrome UX Report data
- Anchor text analysis
- Social engagement metrics
- Website performance indicators
- Competitor SEO metrics

# Features

- Unified REST API
- JSON responses
- Consistent request structure
- Fast integration
- Production-ready endpoints
- Enterprise scalability
- Language-independent implementation
- Developer-friendly documentation
- Comprehensive examples

# Supported APIs

The Enterprise SEO Metrics API currently provides endpoints for:

| API | Description |
|------|-------------|
| Moz Metrics | Domain Authority, Page Authority, Spam Score, backlinks and link metrics |
| Moz Legacy | Legacy Moz metrics for backwards compatibility |
| Ahrefs Metrics | Domain Rating, URL Rating, backlinks, keywords and traffic |
| Semrush Metrics | Authority Score, visibility, traffic and backlink intelligence |
| Majestic Metrics | Trust Flow, Citation Flow and backlink analysis |
| Core Web Vitals | Lighthouse performance and technical SEO metrics |
| Chrome UX Report (CrUX) | Real-world user experience metrics |
| Anchor Text Analysis | Backlink anchor distribution and optimisation insights |
| Social Shares | Website and content social engagement metrics |

Additional endpoints may be introduced in future releases.

# Repository Structure

```
/
├── definitions/
├── endpoints/
├── examples/
├── guides/
├── schemas/
└── README.md
```

| Directory | Purpose |
|-----------|---------|
| [`/definitions`](/definitions) | SEO metric descriptions and terminology |
| [`/endpoints`](/endpoints) | Individual endpoint documentation |
| [`/examples`](/examples) | Request and response examples |
| [`/guides`](/guides) | Integration guides and best practices |
| [`/schemas`](/schemas) | Response schemas and data models |

# Quick Start

Integrating the API typically consists of four steps:

1. Obtain an API key.
2. Authenticate your requests.
3. Send requests to the required endpoint.
4. Parse the JSON response.

Detailed instructions are available in the documentation.

# Authentication

All API requests require authentication.

See [`guides/authentication.md`](guides/authentication.md) for:

- API keys
- Authentication headers
- Security recommendations
- Request signing (if applicable)

# API Endpoints

Endpoint documentation is organised by provider.

| Category | Documentation |
|----------|---------------|
| Moz Metrics | [`/endpoints/moz-metrics.md`](/endpoints/moz-metrics.md) |
| Moz Legacy | [`/endpoints/moz-legacy.md`](/endpoints/moz-legacy.md) |
| Ahrefs Metrics | [`/endpoints/ahrefs-metrics.md`](/endpoints/ahrefs-metrics.md) |
| Semrush Metrics | [`/endpoints/semrush-metrics.md`](/endpoints/semrush-metrics.md) |
| Majestic Metrics | [`/endpoints/majestic-metrics.md`](/endpoints/majestic-metrics.md) |
| Core Web Vitals | [`/endpoints/core-web-vitals.md`](/endpoints/core-web-vitals.md) |
| Chrome UX Report | [`/endpoints/crux-report.md`](/endpoints/crux-report.md) |
| Anchor Text Analysis | [`/endpoints/anchor-text-analysis.md`](/endpoints/anchor-text-analysis.md) |
| Social Shares | [`/endpoints/social-shares.md`](/endpoints/social-shares.md) |

Each endpoint includes:

- Overview
- Request parameters
- Response fields
- Status codes
- Error responses
- Usage notes
- Example requests
- Example responses

# Response Schemas

Complete JSON schemas are available in [`/schemas`](/schemas).

| Endpoint | Documentation |
|----------|---------------|
| Moz Metrics | [`/schemas/moz-metrics.md`](/schemas/moz-metrics.md) |
| Moz Legacy Metrics | [`/schemas/moz-legacy.md`](/schemas/moz-legacy.md) |
| Ahrefs Metrics | [`/schemas/ahrefs-metrics.md`](/schemas/ahrefs-metrics.md) |
| Semrush Metrics | [`/schemas/semrush-metrics.md`](/schemas/semrush-metrics.md) |
| Majestic Metrics | [`/schemas/majestic-metrics.md`](/schemas/majestic-metrics.md) |
| Core Web Vitals | [`/schemas/core-web-vitals.md`](/schemas/core-web-vitals.md) |
| Chrome UX Report | [`/schemas/crux-report.md`](/schemas/crux-report.md) |
| Anchor Text Analysis | [`/schemas/anchor-text.md`](/schemas/anchor-text-analysis.md) |
| Social Shares | [`/schemas/social-shares.md`](/schemas/social-shares.md) |

These schemas describe request and response objects for every endpoint.

# Code Examples

Example implementations are provided for multiple languages.

Available examples include (but are not limited to):

- cURL
- JavaScript
- TypeScript
- Python
- PHP
- C#
- Java
- Go

Examples are located in [`/examples`](/examples).

| Endpoint | Documentation |
|----------|---------------|
| Moz Metrics | [`/examples/moz-metrics.md`](/examples/moz-metrics.md) |
| Moz Legacy Metrics | [`/examples/moz-legacy.md`](/examples/moz-legacy.md) |
| Ahrefs Metrics | [`/examples/ahrefs-metrics.md`](/examples/ahrefs-metrics.md) |
| Semrush Metrics | [`/examples/semrush-metrics.md`](/examples/semrush-metrics.md) |
| Majestic Metrics | [`/examples/majestic-metrics.md`](/examples/majestic-metrics.md) |
| Core Web Vitals | [`/examples/core-web-vitals.md`](/examples/core-web-vitals.md) |
| Chrome UX Report | [`/examples/crux-report.md`](/examples/crux-report.md) |
| Anchor Text Analysis | [`/examples/anchor-text.md`](/examples/anchor-text-analysis.md) |
| Social Shares | [`/examples/social-shares.md`](/examples/social-shares.md) |

# Metric Definitions

The Enterprise SEO Metrics API returns data from multiple SEO and website intelligence sources. This section explains the meaning, calculation context, and intended usage of metrics returned in API responses. Understanding these definitions helps developers correctly interpret SEO data and build accurate reporting, analytics, and automation workflows.

Definitions are organised by data endpoint:

| Endpoint | Documentation |
|----------|---------------|
| Moz Metrics | [`/definitions/moz-metrics.md`](/definitions/moz-metrics.md) |
| Moz Legacy Metrics | [`/definitions/moz-legacy.md`](/definitions/moz-legacy.md) |
| Ahrefs Metrics | [`/definitions/ahrefs-metrics.md`](/definitions/ahrefs-metrics.md) |
| Semrush Metrics | [`/definitions/semrush-metrics.md`](/definitions/semrush-metrics.md) |
| Majestic Metrics | [`/definitions/majestic-metrics.md`](/definitions/majestic-metrics.md) |
| Core Web Vitals | [`/definitions/core-web-vitals.md`](/definitions/core-web-vitals.md) |
| Chrome UX Report | [`/definitions/crux-report.md`](/definitions/crux-report.md) |
| Anchor Text Analysis | [`/definitions/anchor-text.md`](/definitions/anchor-text-analysis.md) |
| Social Shares | [`/definitions/social-shares.md`](/definitions/social-shares.md) |

Each definition includes:

- Metric name
- Description
- Data type
- Example value
- Interpretation
- Common usage scenarios
- Related metrics

# Guides

The [`/guides`](/guides) directory contains additional documentation including:

- Authentication
- Error handling
- Rate limits
- Best practices
- Version migration
- Integration tutorials

## Rate Limits

Rate limits vary depending on your subscription plan.

See [`guides/rate-limits.md`](guides/rate-limits.md) for complete details.

## Error Handling

Error responses follow a consistent JSON structure.

Documentation includes:

- HTTP status codes
- Validation errors
- Authentication errors
- Rate limiting responses
- Internal server errors

See [`guides/error-handling.md`](guides/error-handling.md) for more details.

## Versioning

API changes are versioned to maintain backwards compatibility whenever possible.

See the changelog for release history and migration information.

# Contributing

This repository contains the official documentation for the Enterprise SEO Metrics API. Documentation improvements, corrections and suggestions are more than welcome.

**Please review the contribution guidelines before submitting changes.**

# Support

For technical support, business enquiries or partnership opportunities, please contact the API team through the official website or contact the API team directly on [RapidAPI](https://rapidapi.com/xenoryapi/api/enterprise-seo-metrics).

## License

Unless otherwise stated, the contents of this repository are proprietary documentation for the Enterprise SEO Metrics API. Public access to this repository does not grant permission to reproduce, redistribute or create derivative works from the documentation without prior written permission. Use of the Enterprise SEO Metrics API is governed by the applicable Terms of Service.
