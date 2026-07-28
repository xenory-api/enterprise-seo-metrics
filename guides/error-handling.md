# Error Handling

This guide explains how the **Enterprise SEO Metrics API** reports errors, how to interpret common HTTP status codes, and recommended strategies for building resilient integrations. Understanding the API's error responses allows applications to detect failures, retry requests where appropriate, and provide meaningful feedback to users.

# Table of Contents

- [Overview](#overview)
- [Error Response Format](#error-response-format)
- [HTTP Status Codes](#http-status-codes)
- [Validation Errors (422)](#validation-errors-422)
- [Authentication Errors](#authentication-errors)
- [Server Errors (500)](#server-errors-500)
- [Retry Strategy](#retry-strategy)
- [Troubleshooting](#troubleshooting)

# Overview

The Enterprise SEO Metrics API uses standard HTTP status codes to indicate whether a request completed successfully. That is, successful requests return a `200 OK` response. If a request cannot be processed, the API returns an appropriate HTTP status code together with a structured JSON error object describing the failure.

# Error Response Format

All error responses follow a consistent JSON structure.

```json
{
  "success": false,
  "error": {
    "code": 422,
    "status": "Unprocessable Entity",
    "message": "The URL field is required."
  }
}
```

## Error Object

| Field     | Type    | Description                              |
| --------- | ------- | ---------------------------------------- |
| `code`    | integer | HTTP status code returned by the API.    |
| `status`  | string  | Error status identifier.                 |
| `message` | string  | Human-readable description of the error. |

# HTTP Status Codes

The following status codes may be returned by the Enterprise SEO Metrics API.

| Status                      | Description                                                                  |
| --------------------------- | ---------------------------------------------------------------------------- |
| `200 OK`                    | The request completed successfully.                                          |
| `401 Unauthorized`          | Authentication credentials are missing or invalid.                           |
| `403 Forbidden`             | Your RapidAPI subscription does not permit access to the requested endpoint. |
| `422 Unprocessable Entity`  | One or more required request parameters are missing or invalid.              |
| `500 Internal Server Error` | An unexpected error occurred while processing the request.                   |

# Validation Errors (422)

A `422 Unprocessable Entity` response indicates that the request reached the API but could not be processed because one or more parameters failed validation.

Common causes include:

- Missing required parameters.
- Invalid URL values.
- Empty request body.
- Incorrect parameter names.
- Invalid parameter formats.

Example:

```json
{
  "success": false,
  "error": {
    "code": 422,
    "status": "Unprocessable Entity",
    "message": "The URL field is required."
  }
}
```

To resolve validation errors:

- Verify that all required parameters are included.
- Ensure parameter names match the endpoint documentation exactly.
- Confirm that parameter values use the expected format.
- Refer to the documentation for the specific endpoint being called.

# Authentication Errors

Authentication failures occur before the API processes your request.

## 401 Unauthorized

Returned when authentication credentials are missing or invalid.

Possible causes include:

- Missing `X-RapidAPI-Key` header.
- Invalid or expired API key.
- Incorrect authentication header.

## 403 Forbidden

Returned when authentication succeeds but your RapidAPI subscription does not allow access to the requested endpoint.

Possible causes include:

- The API subscription is inactive.
- The endpoint is unavailable under your current subscription.
- Your RapidAPI account no longer has permission to access the API.

For authentication setup, see:

```text
guides/authentication.md
```

# Server Errors (500)

A `500 Internal Server Error` indicates that an unexpected error occurred while processing the request.

Example:

```json
{
  "success": false,
  "error": {
    "code": 500,
    "status": "Internal Server Error",
    "message": "An unexpected error occurred while processing the request."
  }
}
```

These errors are typically temporary and do not indicate a problem with the request itself.

If the error persists, contact the API provider with:

- The endpoint being called.
- The approximate time of the request.
- The complete error response.
- A reproducible example, if available.

# Retry Strategy

Some errors are temporary and may succeed if the request is attempted again.

General recommendations:

| Code | Status | Description |
|--------|-------------|-------------|
| `200 ` | `OK` | The request completed successfully. |
| `401 ` | `Unauthorized` | Authentication credentials are missing or invalid. |
| `403 ` | `Forbidden` | Your RapidAPI subscription does not permit access to the requested endpoint. |
| `404 ` | `Not Found` | Returned by certain endpoints when the requested resource or dataset is unavailable. |
| `422 ` | `Unprocessable Entity` | One or more required request parameters are missing or invalid. |
| `500 ` | `Internal Server Error` | An unexpected error occurred while processing the request. |

When retrying failed requests:

- Retry only temporary server errors.
- Wait briefly before each retry.
- Use exponential backoff to avoid repeated immediate requests.
- Limit the total number of retry attempts.

# Troubleshooting

The following checklist resolves most integration issues.

| Problem                     | Recommended Action                                                                          |
| --------------------------- | ------------------------------------------------------------------------------------------- |
| Authentication failed       | Verify your API key and required request headers.                                           |
| Invalid request             | Check that all required parameters are present and correctly named.                         |
| Unexpected validation error | Compare your request against the endpoint documentation.                                    |
| Server error                | Retry the request after a short delay.                                                      |
| Unexpected response         | Confirm that you are calling the correct endpoint and using the correct request parameters. |
