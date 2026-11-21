# ADR-0006: Configurable Source Registry

## Status

**Accepted**

## Date

2026-11-21

---

## 1\. Context

LLM Radar must monitor a large and continuously growing number of companies and information sources.

Hardcoding URLs and source configurations directly into application code would make the system difficult to maintain, extend, and scale.

A centralized and configurable source management mechanism is required to support source expansion, source-specific collection strategies, and operational control without requiring application code changes.

## 2\. Decision

Implement a **Database-Driven Source Registry**.

The following decisions have been made:

- All information sources must be registered and managed through a centralized database-driven registry.
- Every collector must use configurable source definitions.
- New sources should be added through database records or administrative APIs whenever possible.
- Source configurations must support different collection methods and source categories.
- Sources must be independently enabled or disabled without modifying application code.
- Source-specific configuration must be maintained independently of collector business logic.

## 3\. Alternatives Considered

The following alternatives were evaluated:

| Alternative | Description |
| --- | --- |
| Hardcoded Source Definitions | Define source URLs and configurations directly within application code. |
| Configuration-Only YAML Files | Maintain source definitions exclusively in YAML configuration files. |
| Separate Collector Code for Every Company | Develop dedicated collection logic for each monitored company. |

## 4\. Consequences

### Positive

- Easier expansion of monitored companies and information sources.
- Centralized source configuration and management.
- Support for source-specific collection settings.
- Ability to enable or disable sources without application code changes.
- Reduced dependency on application deployments for source management.
- Improved maintainability as the number of sources grows.

### Negative

- Requires source configuration validation.
- Different source formats and collection mechanisms require dedicated adapters.
- Introduces additional database relationships and configuration management responsibilities.
- Incorrect source configurations may affect collection reliability.

## 5\. Implementation

The following implementation requirements must be followed:

- Create a dedicated source registry entity in the database.
- Store source-specific collection configurations.
- Associate sources with relevant companies whenever applicable.
- Support different collection methods through configurable source definitions.
- Maintain source category and source type information.
- Store API configuration where required.
- Maintain an active/inactive status for each source.
- Record collection metadata for monitoring and auditing.
- Validate source configurations before enabling collection.
- Ensure collectors retrieve their configuration from the source registry rather than relying on hardcoded definitions.
- Implement dedicated adapters for source-specific formats and collection methods.
- Allow administrative APIs to manage source configurations whenever possible.

### 5.1. Source Registry Data Model

The source registry must support the following attributes:

| Field | Description |
| --- | --- |
| Source Name | Human-readable name of the information source. |
| Source URL | Base URL or endpoint of the information source. |
| Collection Method | Method used to collect information, such as API, RSS, or web scraping. |
| Source Category | Classification of the information source. |
| API Configuration | Source-specific API settings and integration parameters. |
| Company Relationship | Associated company or organization, where applicable. |
| Active Status | Indicates whether the source is enabled or disabled. |
| Collection Metadata | Metadata related to collection execution and source processing. |

### 5.2. Source Management Guidelines

- Source definitions must be maintained centrally.
- Collectors must not depend on hardcoded source URLs.
- Source configurations must be independently maintainable.
- New sources should not require application code changes when existing collection adapters support them.
- Dedicated adapters should be implemented when a source requires a specialized collection mechanism.
- Source configuration changes must be validated before activation.
- Inactive sources must be excluded from scheduled collection workflows.
- Collection metadata should be maintained to support monitoring and troubleshooting.

## 6\. Related ADRs

- **ADR-0005**
- **ADR-0007**
