# ADR-0001: Modular Monolith Architecture

## Status

**Accepted**

## Date

2026-11-21

---

## 1\. Context

LLM Radar will contain several business domains, including data collection, AI intelligence, model management, hardware analysis, reporting, and user management.

Starting with a microservices architecture would introduce unnecessary deployment, networking, monitoring, service communication, and operational complexity during the initial development phase.

A scalable application architecture is required that provides clear separation of business responsibilities while keeping development, deployment, and maintenance manageable.

## 2\. Decision

Adopt a **Modular Monolith Architecture** with clearly separated domain modules.

The following decisions have been made:

- The application will initially be developed and deployed as a single modular backend application.
- Each business domain must maintain clearly defined responsibilities and interfaces.
- Domain modules must remain logically independent.
- Background processing will be separated logically from HTTP request handling.
- Modules must communicate through well-defined interfaces rather than tightly coupled internal dependencies.
- Selected modules may become independent services if future scaling requirements justify extraction.
- The architecture must support future evolution without requiring an immediate transition to microservices.

## 3\. Alternatives Considered

The following alternatives were evaluated:

| Alternative | Description |
| --- | --- |
| Microservices Architecture | Split application domains into independently deployable services. |
| Serverless Architecture | Implement application functionality using independently executed serverless functions. |
| Traditional Monolithic Application | Build the entire application without clearly separated domain modules. |

## 4\. Consequences

### Positive

- Simpler initial development and deployment.
- Easier database transaction management across related business operations.
- Clear separation of business domains and responsibilities.
- Lower initial infrastructure and operational costs.
- Easier debugging and application monitoring.
- Reduced complexity compared with distributed microservices.
- Provides a foundation for future service extraction when necessary.

### Negative

- Requires disciplined module boundaries and dependency management.
- Independent horizontal scaling of individual domain modules is initially limited.
- Poor module separation could lead to tight coupling over time.
- A single deployment unit means changes to one module may require redeployment of the application.

## 5\. Implementation

The following implementation requirements must be followed:

- Organize backend code by business domain rather than creating one large collection of unrelated services.
- Define clear responsibilities for each domain module.
- Maintain well-defined interfaces between modules.
- Avoid direct dependencies on another module's internal implementation details.
- Separate API routing, business logic, data access, and schema definitions.
- Keep background processing logically independent of HTTP request handling.
- Maintain shared infrastructure components without mixing domain-specific business logic.
- Ensure modules can be tested independently wherever practical.
- Document inter-module dependencies and communication patterns.
- Evaluate service extraction only when justified by scaling, deployment, or operational requirements.

### 5.1. Initial Business Domain Modules

The initial backend architecture will support the following business domains:

| Domain Module | Responsibility |
| --- | --- |
| Data Collection | Collect information from registered companies and information sources. |
| AI Intelligence | Perform AI-based classification, extraction, summarization, and analysis. |
| Model Management | Manage AI model information, specifications, and release history. |
| Hardware Analysis | Estimate hardware requirements and analyze model compatibility. |
| Reporting | Generate daily, weekly, and monthly intelligence reports. |
| User Management | Manage user accounts, authentication, and authorization. |

### 5.2. Architecture Guidelines

- Maintain clear domain boundaries.
- Keep business logic inside its respective domain module.
- Use well-defined interfaces for cross-module communication.
- Avoid unnecessary circular dependencies.
- Keep shared utilities and infrastructure separate from domain-specific functionality.
- Use centralized database management while maintaining domain-level data ownership responsibilities.
- Separate long-running background operations from synchronous API processing.
- Design modules to support future independent extraction when required.

### 5.3. Future Scalability Considerations

The modular monolith architecture should support gradual evolution toward independently deployable services.

Potential candidates for future extraction may include:

- Data collection services.
- AI inference and processing services.
- Hardware estimation services.
- Background processing workers.
- Reporting services.

Service extraction must be driven by measurable scaling, deployment, or operational requirements rather than introduced prematurely.

## 6\. Related ADRs

- **ADR-0003**
- **ADR-0005**
- **ADR-0011**
