# Versioning

This guide explains how the **Enterprise SEO Metrics API** manages versions, introduces changes, and maintains compatibility between releases.

Versioning ensures developers can understand when updates occur and determine whether changes require action within their applications.

# Table of Contents

- [Overview](#overview)
- [Current API Version](#current-api-version)
- [Semantic Versioning](#semantic-versioning)
- [Version Components](#version-components)
- [Release Documentation](#release-documentation)
- [Backwards Compatibility](#backwards-compatibility)

# Overview

The **Enterprise SEO Metrics API** uses versioning to provide predictable updates and maintain compatibility for existing integrations. Future releases will follow semantic versioning principles to clearly communicate the impact of changes.

# Current API Version

The current API version is:

```text
v1
```

The version is included in RapidAPI and represents the major API release currently available to developers. Applications should use the documented API version and monitor future releases for updates.

# Semantic Versioning

Small API updates follow Semantic Versioning.

A version number follows this format:

```text
MAJOR.MINOR.PATCH
```

Example:

```text
v1.0.1
```

Each number communicates the type of change introduced.

# Version Components

| Component | Description                                                                    |
| --------- | ------------------------------------------------------------------------------ |
| **MAJOR** | Introduces breaking changes that may require application updates.              |
| **MINOR** | Adds new functionality while maintaining backwards compatibility.              |
| **PATCH** | Includes bug fixes and small improvements without changing existing behaviour. |

Example:

| Version Change      | Meaning                                                    |
| ------------------- | ---------------------------------------------------------- |
| `v1.0.0` → `v2.0.0` | Major release with potentially breaking changes.           |
| `v1.0.0` → `v1.1.0` | New features added without breaking existing integrations. |
| `v1.0.0` → `v1.0.1` | Bug fixes or minor improvements only.                      |

# Release Documentation

All API changes are documented through GitHub Releases.

Each release includes:

- Version number.
- Summary of changes.
- New features.
- Bug fixes.
- Breaking changes (if applicable).
- Migration guidance when required.

Developers should review the **Releases** section of the repository when upgrading API versions.

# Backwards Compatibility

The Enterprise SEO Metrics API aims to maintain backwards compatibility whenever possible.

Changes that preserve existing integrations may include:

- Adding new response fields.
- Introducing new optional parameters.
- Adding new endpoints.
- Improving internal processing.

Breaking changes may include:

- Removing existing fields.
- Changing response structures.
- Changing required request parameters.
- Altering existing endpoint behaviour.

Breaking changes will be introduced through a new major version whenever possible.

Applications should be designed to ignore unknown response fields to remain compatible with future non-breaking updates.