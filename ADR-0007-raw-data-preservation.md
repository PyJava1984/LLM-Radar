# ADR-0007: Raw Data Preservation

## Status

**Accepted**

## Date

2026-11-21

---

## 1\. Context

AI extraction and classification models will evolve over time.

The platform must be able to reprocess historical information without collecting it again. Preserving original source information is essential for improving extraction accuracy, validating AI-generated results, debugging processing errors, and supporting historical analysis.

A data architecture is required to retain original source content independently of normalized business entities.

## 2\. Decision

Maintain a **Raw Document Layer** separate from normalized business entities.

The following decisions have been made:

- Preserve original content or an appropriate source snapshot.
- Store relevant source metadata and the original source URL.
- Record the collection timestamp.
- Generate and maintain a content hash for document integrity and duplicate detection.
- Keep raw documents separate from normalized articles and other business entities.
- Support future reprocessing of historical documents using updated extraction and classification models.

## 3\. Alternatives Considered

The following alternatives were evaluated:

| Alternative | Description |
| --- | --- |
| Store Only Extracted Information | Retain only structured information extracted from original source content. |
| Store Only Summarized Articles | Preserve AI-generated summaries instead of the original source documents. |
| Store Raw Documents in the Same Tables as Normalized Entities | Combine original source content and normalized business information within the same database tables. |

## 4\. Consequences

### Positive

- Supports reprocessing historical information using improved AI models.
- Better data auditability and traceability.
- Improved historical analysis and reporting.
- Easier debugging of extraction and classification errors.
- Preserves original information for future validation.
- Reduces the need to recollect previously acquired information.

### Negative

- Increased storage requirements.
- Requires appropriate data retention and backup policies.
- Third-party content storage must respect applicable licensing restrictions.
- Requires additional data lifecycle and storage management.

## 5\. Implementation

The following implementation requirements must be followed:

- Maintain separate raw document and normalized article entities.
- Preserve original source content or an appropriate source snapshot.
- Store source metadata and original source URLs.
- Record the collection timestamp for each raw document.
- Generate a content hash to support document integrity verification and duplicate detection.
- Maintain relationships between raw documents and their corresponding normalized business entities.
- Ensure raw documents remain available for historical reprocessing, subject to retention policies.
- Implement appropriate backup and retention strategies.
- Ensure third-party content storage complies with applicable licensing and usage restrictions.
- Keep raw document storage independent of AI extraction and classification logic.

### 5.1. Raw Document Metadata

| Field | Description |
| --- | --- |
| Original Content | Original document content or an appropriate source snapshot. |
| Source Metadata | Metadata associated with the original information source. |
| Source URL | Original URL from which the document was collected. |
| Collection Time | Date and time when the document was collected. |
| Content Hash | Hash value used for integrity verification and duplicate detection. |

### 5.2. Data Architecture

The initial data architecture will maintain two separate layers:

| Data Layer | Responsibility |
| --- | --- |
| Raw Document Layer | Preserves original source content, snapshots, and collection metadata. |
| Normalized Entity Layer | Stores structured articles and other normalized business entities extracted from raw documents. |

### 5.3. Future Storage Considerations

- PostgreSQL will initially manage raw document metadata and normalized business entities.
- Large binary files may be stored in object storage in a future deployment.
- Object storage integration should maintain references between stored files and their corresponding database records.
- Storage architecture should support scalable retention, backup, and retrieval operations.

## 6\. Related ADRs

- **ADR-0002**
- **ADR-0013**
