# ADR-0002: PostgreSQL as Primary Database

## Status

**Accepted**

## Date

2026-11-21

---

## 1\. Context

LLM Radar requires a reliable data persistence layer that supports relational data integrity, historical tracking, flexible model metadata, structured relationships, and reporting capabilities.

The database must support complex relationships between companies, AI models, hardware specifications, information sources, extracted articles, and historical records.

A database solution is required that provides strong transactional guarantees while supporting flexible technical specifications and evolving application requirements.

## 2\. Decision

Use **PostgreSQL as the Primary System of Record**.

The following decisions have been made:

- PostgreSQL will serve as the primary relational database.
- JSONB will be used for flexible technical specifications and source-specific metadata.
- SQLAlchemy 2.x will be used for ORM operations and database interactions.
- Alembic will manage database schema migrations.
- Relational constraints and indexes will enforce data integrity and support efficient queries.
- The database architecture must support historical model, release, and hardware information tracking.

## 3\. Alternatives Considered

The following alternatives were evaluated:

| Alternative | Description |
| --- | --- |
| MySQL | Use MySQL as the primary relational database. |
| MongoDB | Use a document-oriented database for flexible data storage. |
| SQLite | Use a lightweight embedded relational database. |
| Multiple Databases from the Beginning | Introduce multiple specialized databases for different application domains during the initial implementation. |

## 4\. Consequences

### Positive

- Strong relational data integrity through foreign keys and constraints.
- JSONB flexibility for storing evolving technical specifications and metadata.
- Reliable transaction support.
- Mature indexing and query optimization capabilities.
- Powerful reporting and analytical query support.
- Suitable for historical model and release tracking.
- Strong integration with Python and SQLAlchemy.
- Support for structured and semi-structured data within a unified database.

### Negative

- Schema migrations require controlled management and versioning.
- Large-scale search may eventually require specialized indexing or a dedicated search service.
- JSONB usage requires careful schema and validation management.
- Database indexing and query performance must be monitored as data volume grows.

## 5\. Implementation

The following implementation requirements must be followed:

- Use PostgreSQL as the primary system of record.
- Use SQLAlchemy 2.x for ORM operations and database persistence.
- Use Alembic for version-controlled database schema migrations.
- Use UUID primary keys for application entities.
- Define foreign key relationships to maintain referential integrity.
- Use `TIMESTAMPTZ` for timezone-aware timestamp storage.
- Apply appropriate unique constraints to prevent duplicate records.
- Create indexes for frequently queried and filtered fields.
- Use JSONB for flexible technical specifications and source-specific metadata.
- Maintain normalized relational structures for core business entities.
- Design database relationships to support historical tracking and reporting.
- Ensure database schema changes are managed through migration scripts.

### 5.1. Database Technology Stack

| Component | Technology |
| --- | --- |
| Primary Database | PostgreSQL |
| ORM | SQLAlchemy 2.x |
| Schema Migration | Alembic |
| Flexible Metadata Storage | JSONB |
| Primary Key Strategy | UUID |
| Timestamp Handling | TIMESTAMPTZ |
| Referential Integrity | Foreign Keys |
| Search Optimization | PostgreSQL Indexes |

### 5.2. Database Design Guidelines

- Use UUID primary keys for application entities.
- Define appropriate foreign key relationships between related entities.
- Apply unique constraints to fields requiring uniqueness.
- Use indexes for frequently accessed and filtered fields.
- Use JSONB for flexible metadata rather than introducing unnecessary schema changes.
- Prefer normalized relational structures for core business data.
- Maintain consistent timestamp handling using `TIMESTAMPTZ`.
- Use database transactions for operations requiring atomicity.
- Manage all schema changes through Alembic migrations.
- Avoid modifying production database schemas manually.
- Design tables to support historical model, release, and hardware information.

### 5.3. Data Integrity and Historical Tracking

The database must support:

- Referential integrity between related business entities.
- Consistent timestamp storage and retrieval.
- Historical tracking of AI models and releases.
- Flexible storage of technical specifications.
- Reliable source and evidence relationships.
- Efficient reporting and analytical queries.
- Controlled schema evolution through migrations.

## 6\. Related ADRs

- **ADR-0007**
- **ADR-0013**
