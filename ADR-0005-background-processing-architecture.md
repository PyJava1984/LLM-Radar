# ADR-0005: Background Processing Architecture

## Status

**Accepted**

## Date

2026-11-21

---

## 1\. Context

Data collection, document extraction, AI inference, and hardware analysis may take longer than normal HTTP request lifecycles.

Executing these operations synchronously within API requests could result in request timeouts, reduced API responsiveness, and difficulties managing failures or retries.

A dedicated background processing architecture is required to handle long-running operations independently of normal HTTP request processing.

## 2\. Decision

Execute long-running operations through **Background Workers**.

The following decisions have been made:

- Long-running operations must execute asynchronously through background workers.
- PostgreSQL-backed job tracking will be used initially.
- A dedicated message broker and task queue, such as Redis with Celery or another suitable worker system, may be introduced when workload requirements justify it.
- n8n will initiate and coordinate workflows but will not perform core application processing.
- Background workers will handle computationally intensive and long-running application tasks.
- Job execution must support status tracking, retries, and failure management.

## 3\. Alternatives Considered

The following alternatives were evaluated:

| Alternative | Description |
| --- | --- |
| Synchronous API Processing | Execute long-running operations directly within HTTP API requests. |
| In-Process Background Tasks Only | Use background tasks within the application process without dedicated worker infrastructure. |
| Celery from the Beginning | Introduce Celery and a dedicated message broker as part of the initial architecture. |
| Distributed Event Streaming Infrastructure | Use distributed event streaming infrastructure for asynchronous task coordination and processing. |

## 4\. Consequences

### Positive

- Improved API responsiveness by separating long-running operations from HTTP request lifecycles.
- Support for retry mechanisms and failure recovery.
- Independent worker execution and horizontal scalability.
- Better control over background job execution.
- Improved operational visibility through job lifecycle tracking.
- Reduced risk of API request timeouts during intensive processing.

### Negative

- Introduces additional job lifecycle management responsibilities.
- Requires idempotency to prevent duplicate processing.
- Requires execution tracking and failure monitoring.
- Additional infrastructure may be required as processing workloads grow.

## 5\. Implementation

The following implementation requirements must be followed:

- Implement background workers for long-running application operations.
- Use PostgreSQL-backed job tracking during the initial implementation.
- Maintain a centralized job lifecycle management mechanism.
- Support job status transitions and execution tracking.
- Implement retry handling for recoverable failures.
- Ensure background tasks are designed to be idempotent wherever possible.
- Keep core processing logic independent of n8n workflow orchestration.
- Use n8n to initiate, coordinate, and monitor application workflows.
- Introduce a dedicated message broker and task queue when workload requirements justify it.
- Maintain execution logs and failure details for troubleshooting.
- Ensure workers can execute independently of the FastAPI application process.

### 5.1. Background Job Lifecycle

The job tracking mechanism should support the following lifecycle states:

| Status | Description |
| --- | --- |
| `PENDING` | Job has been created and is waiting for execution. |
| `RUNNING` | Job is currently being processed by a worker. |
| `COMPLETED` | Job has completed successfully. |
| `FAILED` | Job execution has failed. |
| `RETRYING` | Job is scheduled for another execution attempt. |

### 5.2. Job Tracking Metadata

The following metadata must be tracked for background job execution:

| Field | Description |
| --- | --- |
| Job Status | Current lifecycle status of the job. |
| Retry Count | Number of execution attempts. |
| Execution ID | Unique identifier associated with the job execution. |
| Start Time | Date and time when job execution started. |
| Completion Time | Date and time when job execution finished. |
| Failure Details | Error information associated with failed execution. |

### 5.3. Processing Responsibilities

| Component | Responsibility |
| --- | --- |
| FastAPI | Accept API requests and initiate background operations. |
| PostgreSQL | Maintain job records, execution metadata, and job status. |
| Background Workers | Execute long-running application processing tasks. |
| n8n | Initiate and coordinate automated workflows. |
| Redis / Message Broker | Provide task messaging and queue management when introduced. |
| Celery / Worker System | Manage distributed task execution when introduced. |

### 5.4. Background Processing Guidelines

- Avoid executing computationally intensive operations directly within HTTP request lifecycles.
- Ensure jobs can be safely retried without unintended duplicate side effects.
- Maintain accurate job execution status and timestamps.
- Capture meaningful failure details for debugging and monitoring.
- Keep workflow orchestration separate from core application processing.
- Design workers to support independent deployment and scaling.
- Introduce additional queue infrastructure only when justified by workload requirements.

## 6\. Related ADRs

- **ADR-0001**
- **ADR-0004**
- **ADR-0011**
