# ADR-0012: Versioned REST API

## Status

**Accepted**

## Date

2026-11-21

---

## 1\. Context

The platform has multiple consumers, including the frontend, n8n workflow orchestration, external integrations, and potentially third-party applications.

A consistent and well-defined API contract is required to support communication between these components while allowing the backend to evolve without disrupting existing integrations.

## 2\. Decision

Use **REST APIs with explicit versioning**.

The initial API version prefix will be:

text

```text
/api/v1
```

The following decisions have been made:

- All application API endpoints must follow a versioned URL structure.
- The initial API version will be `v1`.
- API contracts must remain consistent across frontend and external integrations.
- Breaking API changes must be introduced through appropriate version planning.

## 3\. Alternatives Considered

The following alternatives were evaluated:

| Alternative | Description |
| --- | --- |
| Unversioned REST API | Expose REST endpoints without explicit API versioning. |
| GraphQL | Use a GraphQL API instead of REST-based endpoints. |
| Direct Database Access from Frontend Services | Allow frontend services to communicate directly with the database instead of using backend APIs. |

## 4\. Consequences

### Positive

- Stable integration contracts between application components.
- Easier API evolution and backward compatibility management.
- Clear separation between frontend and backend responsibilities.
- Better support for external integrations.
- Consistent API structure across different consumers.

### Negative

- API compatibility must be maintained across versions.
- Breaking changes require proper version planning and migration.
- Multiple API versions may need to be maintained simultaneously.

## 5\. Implementation

The following implementation requirements must be followed:

- Use versioned REST API endpoints with `/api/v1` as the initial prefix.
- Use Pydantic schemas for request validation and response serialization.
- Provide OpenAPI documentation for API endpoints.
- Implement pagination for endpoints returning collections of records.
- Use consistent error response structures across API endpoints.
- Apply authentication and authorization to protected endpoints.
- Maintain clear separation between API routes, business logic, and data access layers.
- Ensure API changes follow backward compatibility guidelines.
- Plan new API versions when introducing breaking changes.

### 5.1. API Configuration

| Setting | Value |
| --- | --- |
| API Architecture | REST |
| Initial API Version | v1 |
| API Prefix | `/api/v1` |
| Request Validation | Pydantic |
| API Documentation | OpenAPI |
| Pagination | Supported |
| Error Handling | Consistent Error Responses |
| Authentication | JWT-based Authentication |

### 5.2. API Design Guidelines

- Use resource-oriented endpoint naming.
- Follow consistent HTTP method conventions (`GET`, `POST`, `PUT`, `PATCH`, and `DELETE`).
- Validate incoming requests using Pydantic schemas.
- Return predictable and consistent response structures.
- Document API endpoints, parameters, and response schemas using OpenAPI.
- Implement pagination for collection endpoints.
- Avoid introducing breaking changes within an existing API version.
- Maintain backward compatibility for existing integrations whenever possible.

## 6\. Related ADRs

- **ADR-0003**
- **ADR-0004**
- **ADR-0010**
