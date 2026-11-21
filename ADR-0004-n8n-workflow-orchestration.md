# ADR-0004: n8n Workflow Orchestration

## Status

**Accepted**

## Date

2026-11-21

---

## 1\. Context

The system requires automated and scheduled operations, including data collection, retry handling, notifications, and periodic report generation.

A centralized workflow orchestration platform is needed to coordinate these operations, manage execution schedules, and provide visibility into workflow execution.

The orchestration layer must remain separate from core application business logic to ensure maintainability and a clear separation of responsibilities.

## 2\. Decision

Use **n8n as the Workflow Orchestration Platform**.

The following decisions have been made:

- n8n will manage scheduled workflows and automated process coordination.
- Core business logic must remain inside Python backend services.
- n8n must communicate with the backend through authenticated API endpoints.
- Workflow execution must support scheduling, retries, notifications, and execution monitoring.
- Workflow definitions must be exportable and maintained in version control.
- n8n must orchestrate application operations without duplicating business logic.

## 3\. Alternatives Considered

The following alternatives were evaluated:

| Alternative | Description |
| --- | --- |
| Linux Cron | Use operating system cron jobs to execute scheduled tasks. |
| APScheduler | Use a Python-based scheduling library for application-level task scheduling. |
| Celery Beat | Use Celery Beat for scheduling distributed background tasks. |
| Airflow | Use Apache Airflow for workflow orchestration and dependency management. |
| Custom Python Scheduling | Implement a custom scheduling and workflow execution mechanism using Python. |

## 4\. Consequences

### Positive

- Visual workflow management and easier operational oversight.
- Simplified scheduling and integration with external services.
- Built-in workflow execution monitoring.
- Support for automated notifications and integrations.
- Easier coordination of multi-step collection and reporting workflows.
- Reduced need to implement scheduling infrastructure directly within application code.

### Negative

- Introduces an additional infrastructure component.
- Workflow versioning and credential management must be handled carefully.
- Workflow execution must not become a second source of business logic.
- Requires coordination between workflow definitions and backend API contracts.

## 5\. Implementation

The following implementation requirements must be followed:

- Use n8n for scheduled workflow execution and orchestration.
- Keep business logic and data processing inside Python backend services.
- Integrate n8n with FastAPI through authenticated API endpoints.
- Configure workflows for scheduled data collection and periodic reporting.
- Implement appropriate retry handling for recoverable workflow failures.
- Use n8n for notification and external service integrations.
- Maintain workflow execution identifiers for tracking and debugging.
- Store exportable workflow JSON definitions in the project repository.
- Manage workflow credentials securely using n8n credential management.
- Version-control workflow definitions to support change tracking and deployment.
- Ensure workflow execution does not duplicate backend business logic.

### 5.1. Workflow Responsibilities

| Component | Responsibility |
| --- | --- |
| n8n | Workflow orchestration, scheduling, and process coordination. |
| FastAPI | Backend API endpoints and business logic execution. |
| Python Services | Data collection, extraction, AI processing, and reporting logic. |
| PostgreSQL | Persistent application data and execution metadata. |
| Background Workers | Execute long-running processing tasks asynchronously. |

### 5.2. Workflow Management Guidelines

- Store exportable workflow JSON files in the repository.
- Use authenticated API communication between n8n and backend services.
- Maintain unique execution identifiers for workflow tracking.
- Keep workflow configurations separate from application business logic.
- Use centralized credential management for external integrations.
- Implement retry and failure-handling strategies.
- Maintain clear workflow naming and documentation conventions.
- Ensure workflow changes are reviewed and version-controlled.
- Avoid embedding complex business rules directly inside n8n workflows.

### 5.3. Initial Workflow Categories

The orchestration platform should support the following workflow categories:

| Workflow Category | Responsibility |
| --- | --- |
| Scheduled Data Collection | Initiate periodic collection from registered information sources. |
| Retry Management | Coordinate retries for failed or incomplete operations. |
| AI Processing Coordination | Initiate backend AI extraction, classification, and analysis operations. |
| Notification Workflows | Send operational alerts and processing notifications. |
| Periodic Reporting | Trigger daily, weekly, and monthly report generation. |

## 6\. Related ADRs

- **ADR-0005**
- **ADR-0015**
