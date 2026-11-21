# ADR-0003: FastAPI Backend Architecture

## Status

**Accepted**

## Date

2026-11-21

---

## 1\. Context

LLM Radar requires a centralized API layer to support communication between the frontend, n8n workflow orchestration, data collectors, reporting services, and external integrations.

The backend must provide a maintainable architecture for business logic, data processing, authentication, API validation, and integration with AI services.

A framework with strong Python ecosystem support, asynchronous capabilities, and automatic API documentation is required.

## 2\. Decision

Use **Python and FastAPI as the Primary Backend Framework**.

The following decisions have been made:

- Python will be the primary backend programming language.
- FastAPI will serve as the primary backend API framework.
- Pydantic will handle request validation, response serialization, and data schema definitions.
- SQLAlchemy will manage database interactions and persistence.
- The backend will be organized into domain-oriented modules.
- API endpoints will follow a versioned REST architecture.
- Business logic must remain separated from API routing and data access responsibilities.

## 3\. Alternatives Considered

The following alternatives were evaluated:

| Alternative | Description |
| --- | --- |
| Django REST Framework | Use Django and its REST Framework for backend API development. |
| Flask | Use Flask as a lightweight Python web framework. |
| Node.js / Express | Use Node.js and Express for backend API development. |
| NestJS | Use NestJS as a structured Node.js backend framework. |

## 4\. Consequences

### Positive

- Strong Python ecosystem support for AI, machine learning, and data processing.
- Automatic OpenAPI documentation generation.
- Pydantic-based request validation and response serialization.
- Support for asynchronous HTTP integrations.
- Clear separation of application components through domain-oriented architecture.
- Easier integration with Python-based AI and data processing libraries.
- Strong support for building REST APIs and external service integrations.

### Negative

- Requires explicit architectural decisions for authentication and authorization.
- Requires database migration management.
- Requires a separate strategy for background processing and task execution.
- Application architecture must be carefully maintained as the number of domains grows.

## 5\. Implementation

The following implementation requirements must be followed:

- Use Python as the primary backend programming language.
- Use FastAPI for API development.
- Use Pydantic for request validation and response schemas.
- Use SQLAlchemy for database interactions and persistence.
- Organize backend functionality into domain-oriented modules.
- Separate API routes, business logic, data access, and schema definitions.
- Expose versioned REST API endpoints under `/api/v1`.
- Implement centralized authentication and authorization dependencies.
- Integrate database migrations for schema version management.
- Support asynchronous HTTP communication where appropriate.
- Maintain OpenAPI documentation for backend endpoints.
- Keep application business logic independent of API framework-specific implementations wherever practical.
- Integrate background workers for long-running operations.

### 5.1. Backend Technology Stack

| Component | Technology |
| --- | --- |
| Programming Language | Python |
| Backend Framework | FastAPI |
| Data Validation | Pydantic |
| ORM / Persistence | SQLAlchemy |
| API Architecture | REST |
| API Versioning | `/api/v1` |
| API Documentation | OpenAPI / Swagger |
| Database | PostgreSQL |
| Background Processing | Dedicated Background Workers |

### 5.2. Backend Architecture Guidelines

- Organize modules around business domains rather than technical layers alone.
- Keep API route handlers lightweight.
- Place business rules and processing logic inside dedicated service modules.
- Use repositories or dedicated data access components for database operations where appropriate.
- Define Pydantic schemas for API requests and responses.
- Centralize authentication and authorization mechanisms.
- Maintain consistent API response and error structures.
- Use dependency injection for shared application services.
- Keep database models separate from API response schemas.
- Ensure modules remain independently maintainable and testable.

### 5.3. API Design Guidelines

- Use versioned REST endpoints under `/api/v1`.
- Follow consistent HTTP method conventions.
- Validate incoming requests using Pydantic.
- Return predictable response structures.
- Implement appropriate HTTP status codes.
- Provide pagination for collection endpoints.
- Document API endpoints through OpenAPI.
- Maintain backward compatibility within existing API versions.

## 6\. Related ADRs

- **ADR-0001**
- **ADR-0005**
- **ADR-0012**
