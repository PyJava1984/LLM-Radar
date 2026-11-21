# ADR-0015: Timezone-Aware Scheduling

## Status

**Accepted**

## Date

2026-11-21

---

## 1\. Context

LLM Radar must perform automated data collection and reporting every day at midnight.

The execution time must remain consistent with the configured operational timezone, regardless of the server's local timezone or deployment environment.

The scheduling system must support predictable daily, weekly, and monthly reporting periods.

## 2\. Decision

Use a configurable timezone for workflow scheduling.

The initial operational timezone will be:

env

```env
TIMEZONE=Asia/Dhaka
```

The following decisions have been made:

- The daily collection workflow will execute at **00:00 (midnight) local time**.
- All database timestamps will be stored using UTC-aware timestamps (`TIMESTAMPTZ`).
- The application must convert between the configured operational timezone and UTC when processing scheduled jobs and calculating reporting periods.

## 3\. Alternatives Considered

The following alternatives were evaluated:

| Alternative | Description |
| --- | --- |
| Fixed UTC Scheduling | Execute workflows at a fixed UTC time. |
| Server-Local Timezone | Use the timezone configured on the deployment server. |
| Hardcoded Application Timezone | Define the timezone directly in application code. |

## 4\. Consequences

### Positive

- Consistent reporting periods.
- Predictable local execution.
- Portable deployment across different environments.
- Centralized timezone configuration.
- Standardized UTC timestamp storage.

### Negative

- Requires timezone-aware date and time calculations.
- Weekly and monthly report generation must handle local calendar boundaries.
- Reporting queries require timezone conversion.
- Scheduling configuration must remain consistent across services.

## 5\. Implementation

The following implementation requirements must be followed:

- Configure the operational timezone through environment variables.
- Use `Asia/Dhaka` as the initial default timezone.
- Use timezone-aware scheduling in n8n.
- Schedule the daily collection workflow at **00:00 local time**.
- Store all database timestamps using UTC-aware `TIMESTAMPTZ` fields.
- Convert reporting date boundaries from the configured local timezone to UTC before querying PostgreSQL.
- Apply timezone-aware calculations to daily, weekly, and monthly reports.
- Avoid hardcoding timezone values in application business logic.

### 5.1. Example Configuration

env

```env
TIMEZONE=Asia/Dhaka
```

### 5.2. Scheduling Configuration

| Setting | Value |
| --- | --- |
| Workflow | Daily AI Intelligence |
| Execution Time | 00:00 |
| Timezone | Asia/Dhaka |
| Frequency | Daily |

### 5.3. Timestamp Handling

| Operation | Timezone |
| --- | --- |
| Workflow Scheduling | Configured operational timezone |
| Daily Reporting | Configured operational timezone |
| Weekly Reporting | Configured operational timezone |
| Monthly Reporting | Configured operational timezone |
| Database Storage | UTC |

## 6\. Related ADRs

- **ADR-0002:** PostgreSQL as Primary Database
- **ADR-0004:** n8n Workflow Orchestration
