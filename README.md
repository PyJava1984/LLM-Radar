# 🚀 LLM Radar

### AI Intelligence & Technology Monitoring Platform

**Discover. Monitor. Analyze. Compare. Understand.**

LLM Radar is a self-hosted, extensible AI intelligence platform designed to continuously monitor, collect, normalize, analyze, and report developments across the global Artificial Intelligence ecosystem.

The platform provides centralized intelligence about:

- Large Language Models (LLMs).
- Small Language Models (SLMs).
- Open-source and proprietary AI models.
- Generative AI technologies.
- AI agents and agentic frameworks.
- AI development frameworks and libraries.
- AI infrastructure and inference engines.
- AI hardware and GPU accelerators.
- Academic research and technical publications.
- AI company announcements and product releases.

LLM Radar integrates information from official company websites, release notes, technical blogs, GitHub, Hugging Face, arXiv, YouTube, Reddit, Hacker News, and other configurable information sources.

Collected information is processed through an AI intelligence pipeline to identify new releases, extract model specifications, detect technology changes, generate technical summaries, estimate hardware requirements, and produce historical intelligence reports.

The platform provides daily, weekly, and monthly intelligence through a centralized web application.

---

## 📑 Table of Contents

- 1\. Project Vision
- 2\. Architectural Principles
- 3\. Architecture Decision Records (ADRs)
- 4\. High-Level System Architecture
- 5\. Architectural Layers
- 6\. Information Sources
- 7\. Data Processing Architecture
- 8\. Core Domain Architecture
- 9\. Database Architecture
- 10\. AI Intelligence Engine
- 11\. Hardware Intelligence Engine
- 12\. Backend Architecture
- 13\. Automation Architecture
- 14\. Frontend Architecture
- 15\. Security Architecture
- 16\. Observability and Reliability
- 17\. Deployment Architecture
- 18\. Project Structure
- 19\. Technology Stack
- 20\. Installation and Setup
- 21\. API Architecture
- 22\. Reporting and Dashboard
- 23\. Development Roadmap
- 24\. Non-Functional Requirements
- 25\. Future Enhancements
- 26\. Contribution Guidelines
- 27\. License
- 28\. Project Mission
- Project Information

---

## 📌 1. Project Vision

### 1.1 Purpose

The objective is to build a centralized intelligence system that provides a continuously updated view of the global AI ecosystem.

Instead of manually monitoring hundreds of companies, websites, repositories, research publications, and media channels, LLM Radar automates the entire intelligence lifecycle.

The platform must answer:

- What new AI models and technologies have been released?
- Which company or organization released them?
- When were they announced or published?
- What has changed compared with previous versions?
- Is the technology open-source, open-weight, or proprietary?
- What are its technical capabilities and limitations?
- What hardware is required to run it?
- How much GPU VRAM and system RAM are needed?
- Which GPUs and inference frameworks are compatible?
- What quantization options are available?
- What is the estimated local or cloud inference cost?
- Which developments are important to the AI industry?

### 1.2 Project Objectives

- Monitor global AI and LLM developments.
- Track open-source and commercial model releases.
- Discover AI technologies and development frameworks.
- Monitor official company announcements and changelogs.
- Track GitHub repositories and Hugging Face models.
- Monitor research papers and technical publications.
- Discover relevant technical videos and community discussions.
- Detect model versions and technology releases.
- Extract structured model specifications.
- Analyze hardware requirements.
- Estimate VRAM, RAM, and storage requirements.
- Analyze GPU and inference framework compatibility.
- Estimate inference costs.
- Generate daily, weekly, and monthly intelligence reports.
- Provide an interactive web application.

---

## 🏗️ 2. Architectural Principles

LLM Radar will follow these architectural principles:

| Principle | Architectural Decision |
| --- | --- |
| Modularity | Domain-oriented modular monolith |
| Maintainability | Clear separation of responsibilities |
| Extensibility | Configurable source registry |
| API First | FastAPI as central application interface |
| Data Integrity | PostgreSQL as primary system of record |
| Traceability | Preserve original sources and evidence |
| Automation | n8n for workflow orchestration |
| Scalability | Background processing and asynchronous workloads |
| Reliability | Retries, idempotency, and execution tracking |
| Security | Authentication, authorization, and secret management |
| Observability | Structured logging and execution monitoring |
| Reproducibility | Versioned processing and migrations |

### 2.1 Architecture Style

LLM Radar will initially use a **Modular Monolith** architecture supported by event-driven processing patterns.

This provides a balance between development simplicity, maintainability, and future scalability.

The application will be organized into independently maintained business modules:

- Source Management.
- Data Collection.
- Content Normalization.
- Intelligence Processing.
- Model Management.
- Technology Management.
- Hardware Intelligence.
- Reporting.
- User Management.
- Notifications.

Each module will have clearly defined responsibilities and interfaces.

Selected workloads can be extracted into independent services when future scaling requirements justify it.

---

## 🧭 3. Architecture Decision Records (ADRs)

LLM Radar uses Architecture Decision Records to document important technical and architectural decisions.

An ADR records:

- The architectural problem.
- The context behind the decision.
- The selected solution.
- Alternative solutions considered.
- Advantages and disadvantages.
- Technical and operational consequences.
- Implementation implications.

### 3.1 ADR Principles

- Every major architectural decision must be documented.
- ADRs must be stored in version control.
- Each ADR must have a unique sequential identifier.
- ADRs must explain the reasoning behind decisions.
- Rejected alternatives must be documented.
- Accepted decisions should not be silently changed.
- Superseded ADRs must remain available for historical reference.
- Changes to accepted decisions require a new ADR.
- ADRs should be reviewed before implementing affected components.
- Decisions must be updated when implementation requirements change.

### 3.2 ADR Status Lifecycle

| Status | Description |
| --- | --- |
| Proposed | Decision is under consideration |
| Accepted | Decision approved |
| Rejected | Proposed decision not selected |
| Superseded | Replaced by a newer decision |
| Deprecated | No longer applicable |

### 3.3 Initial ADR Register

| ADR | Architectural Decision | Status |
| --- | --- | --- |
| ADR-0001 | Modular Monolith Architecture | Accepted |
| ADR-0002 | PostgreSQL as Primary Database | Accepted |
| ADR-0003 | FastAPI Backend Architecture | Accepted |
| ADR-0004 | n8n Workflow Orchestration | Accepted |
| ADR-0005 | Background Processing Architecture | Accepted |
| ADR-0006 | Configurable Source Registry | Accepted |
| ADR-0007 | Raw Data Preservation | Accepted |
| ADR-0008 | AI Provider Abstraction | Accepted |
| ADR-0009 | Hardware Estimation Architecture | Accepted |
| ADR-0010 | Next.js Frontend | Accepted |
| ADR-0011 | Docker-Based Deployment | Accepted |
| ADR-0012 | Versioned REST API | Accepted |
| ADR-0013 | Data Provenance and Evidence Tracking | Accepted |
| ADR-0014 | Authentication and Authorization | Accepted |
| ADR-0015 | Timezone-Aware Scheduling | Accepted |

> **Note:** Accepted indicates the intended architectural baseline. Implementation details and production suitability must be validated during the relevant development phase.

### 3.4 ADR Documentation Location

All ADR documents must be maintained in:

text

```text
docs/adr/
```

Naming convention:

text

```text
ADR-NNNN-short-description.md
```

Examples:

text

```text
ADR-0001-modular-monolith.md
ADR-0002-postgresql.md
ADR-0005-background-processing.md
```

ADR identifiers must never be reused.

### 3.5 ADR Review Process

1. Identify the architectural problem.
2. Review existing ADRs.
3. Identify possible alternatives.
4. Evaluate technical and operational consequences.
5. Create a new ADR or propose an amendment.
6. Review and approve the decision.
7. Implement the decision.
8. Update architecture documentation.

---

## 🏛️ 4. High-Level System Architecture

### 4.1 System Context

The platform integrates external information providers, automation services, backend processing, database infrastructure, and a web application.

#### System Context Diagram

mermaid

```mermaid
flowchart TB
    subgraph SOURCES["External Information Sources"]
        A["Official Company Websites"]
        B["RSS / Release Notes"]
        C["GitHub"]
        D["Hugging Face"]
        E["arXiv / Research"]
        F["YouTube"]
        G["Reddit / Hacker News"]
        H["Technology News"]
    end

    subgraph ORCHESTRATION["Automation Layer"]
        N["n8n Scheduler"]
        W["Workflow Orchestration"]
    end

    subgraph BACKEND["Python Backend"]
        API["FastAPI"]
        COL["Collection Services"]
        NOR["Normalization"]
        INT["AI Intelligence Engine"]
        MOD["Model & Technology Services"]
        HW["Hardware Intelligence"]
        REP["Reporting Engine"]
    end

    subgraph STORAGE["Persistence Layer"]
        RAW[("Raw Documents")]
        DB[("PostgreSQL")]
        LOG[("Execution & Audit Logs")]
    end

    subgraph PRESENTATION["Presentation Layer"]
        WEB["Next.js Dashboard"]
        AUTH["Authentication"]
        REPORT["Daily / Weekly / Monthly Reports"]
    end

    SOURCES --> N
    N --> W
    W --> API
    API --> COL
    COL --> RAW
    COL --> NOR
    NOR --> INT
    INT --> MOD
    MOD --> HW
    HW --> DB
    NOR --> DB
    INT --> DB
    API --> LOG
    DB --> REP
    API --> WEB
    WEB --> AUTH
    WEB --> REPORT
```

### 4.2 Architecture Components

| Component | Responsibility |
| --- | --- |
| External Sources | Provide AI and technology information |
| n8n | Schedule and orchestrate workflows |
| FastAPI | Central application interface |
| Collectors | Retrieve information |
| Normalization | Convert source content into consistent structures |
| Intelligence Engine | Classify and analyze information |
| Hardware Engine | Estimate hardware requirements |
| PostgreSQL | Persist structured and historical data |
| Background Workers | Execute long-running operations |
| Next.js | Present information to users |

### 4.3 Architectural Boundaries

- External systems provide information but do not control internal business logic.
- n8n coordinates workflows but does not own domain logic.
- FastAPI exposes application capabilities.
- Domain modules own their business operations.
- PostgreSQL remains the primary source of truth.
- The frontend accesses backend APIs rather than querying the database directly.

---

## 🧱 5. Architectural Layers

### 5.1 External Information Layer

Responsible for discovering information from external organizations and platforms.

Supported source categories:

| Category | Sources |
| --- | --- |
| Official announcements | AI company websites and blogs |
| Product updates | Product changelogs and release notes |
| Source code | GitHub and GitLab |
| Model repositories | Hugging Face and ModelScope |
| Research | arXiv, OpenReview, Semantic Scholar |
| Video | YouTube |
| Community | Reddit, Hacker News, GitHub Discussions |
| Technology news | TechCrunch, The Verge, VentureBeat, IEEE Spectrum |
| Developer ecosystem | PyPI and framework documentation |

**Collection strategies:**

- Official APIs.
- RSS and Atom feeds.
- Public release endpoints.
- Permitted website crawling.
- Structured metadata extraction.
- Authorized video metadata and transcripts.

Every integration must respect API quotas, licensing, copyright, website terms, and applicable crawling restrictions.

### 5.2 Automation and Orchestration Layer

**Technology:** n8n

Responsibilities:

- Daily scheduling.
- Workflow execution.
- Triggering collection processes.
- Coordinating processing stages.
- Retry management.
- Failure notifications.
- Report generation triggers.
- Monitoring workflow execution.

**Default schedule:**

text

```text
Execution: 00:00 every day
Timezone:  Asia/Dhaka
```

The timezone must be configurable.

n8n communicates with the backend through authenticated API endpoints.

### 5.3 Application Layer

**Technology:** Python + FastAPI

Responsibilities:

- API routing.
- Request validation.
- Authentication and authorization.
- Business service orchestration.
- Database transaction management.
- Collector execution.
- Intelligence processing.
- Report generation.
- External API integration.
- Error handling.

### 5.4 Intelligence Processing Layer

Responsible for transforming unstructured information into structured AI intelligence.

Components:

- Content classification.
- Release detection.
- Entity extraction.
- Company identification.
- Model identification.
- Version extraction.
- Technology categorization.
- Summarization.
- Historical comparison.
- Relevance analysis.
- Duplicate detection.

AI-generated information must be distinguishable from verified source information.

### 5.5 Hardware Intelligence Layer

Responsible for understanding computational requirements of AI models.

It analyzes:

- Model parameters.
- Model architecture.
- Precision formats.
- Quantization formats.
- GPU VRAM.
- System RAM.
- KV cache.
- Storage requirements.
- GPU compatibility.
- Multi-GPU configurations.
- Inference framework compatibility.
- Local inference feasibility.
- Cloud inference cost.

### 5.6 Persistence Layer

**Technology:** PostgreSQL

PostgreSQL stores:

- Users and permissions.
- Companies and organizations.
- Information sources.
- Original collected documents.
- Normalized articles.
- Model information.
- Model versions.
- Technology releases.
- Research publications.
- Hardware specifications.
- Compatibility information.
- AI-generated analysis.
- Reports.
- Collection execution history.
- Audit logs.

Use JSONB for flexible source metadata and model specifications while keeping important business entities relational.

### 5.7 Presentation Layer

**Technology:** Next.js + React + TypeScript

Responsibilities:

- Dashboard.
- Search and discovery.
- Model catalog.
- Company directory.
- Technology tracking.
- Release history.
- Hardware advisor.
- Daily reports.
- Weekly reports.
- Monthly reports.
- Source management.
- User preferences.

---

## 🌐 6. Information Sources

The source registry must be extensible and configurable.

### 6.1 Official AI Companies

Initial coverage:

| Company | Areas to Monitor |
| --- | --- |
| OpenAI | GPT, reasoning models, APIs |
| Google DeepMind | Gemini, Gemma, research |
| Anthropic | Claude and APIs |
| Meta | Llama, PyTorch, research |
| Microsoft | Azure AI, Phi, Copilot |
| NVIDIA | Nemotron, CUDA, TensorRT |
| Amazon AWS | Bedrock, Nova, infrastructure |
| Apple | Apple Intelligence, MLX |
| xAI | Grok |
| DeepSeek | Foundation models |
| Alibaba | Qwen |
| Baidu | ERNIE |
| Tencent | Hunyuan |
| Mistral AI | Mistral and Mixtral |
| Cohere | Command models |
| IBM | Granite and watsonx |
| Stability AI | Generative AI |
| Black Forest Labs | FLUX |
| AI21 Labs | Language models |
| Databricks | Mosaic AI |
| Hugging Face | Open models and tools |

Additional companies must be added through the source and company registry.

### 6.2 Official Information Sources

| Organization | Official Source |
| --- | --- |
| OpenAI | [OpenAI News](<https://openai.com/news/>) |
| Google DeepMind | [Google DeepMind](<https://deepmind.google/>) |
| Anthropic | [Anthropic News](<https://www.anthropic.com/news>) |
| Meta | [Meta AI](<https://ai.meta.com/>) |
| Microsoft | [Microsoft AI](<https://blogs.microsoft.com/ai/>) |
| NVIDIA | [NVIDIA News](<https://nvidianews.nvidia.com/>) |
| AWS | [AWS Machine Learning Blog](<https://aws.amazon.com/blogs/machine-learning/>) |
| Apple | [Apple ML Research](<https://machinelearning.apple.com/>) |
| Mistral | [Mistral News](<https://mistral.ai/news/>) |
| Cohere | [Cohere Blog](<https://cohere.com/blog>) |
| IBM | [IBM Research](<https://research.ibm.com/>) |
| Hugging Face | [Hugging Face Blog](<https://huggingface.co/blog>) |

Also monitor official documentation, release notes, API changelogs, engineering blogs, and GitHub organizations.

### 6.3 Research Sources

| Source | URL |
| --- | --- |
| arXiv | [https://arxiv.org/](<https://arxiv.org/>) |
| Papers with Code | [https://paperswithcode.com/](<https://paperswithcode.com/>) |
| Semantic Scholar | [https://www.semanticscholar.org/](<https://www.semanticscholar.org/>) |
| OpenReview | [https://openreview.net/](<https://openreview.net/>) |
| ACL Anthology | [https://aclanthology.org/](<https://aclanthology.org/>) |
| Google Research | [https://research.google/](<https://research.google/>) |
| Microsoft Research | [https://www.microsoft.com/en-us/research/](<https://www.microsoft.com/en-us/research/>) |
| NVIDIA Research | [https://research.nvidia.com/](<https://research.nvidia.com/>) |

Relevant categories:

- `cs.AI`
- `cs.CL`
- `cs.LG`
- `cs.CV`
- `cs.RO`
- `stat.ML`

### 6.4 Open-Source Platforms

| Platform | URL |
| --- | --- |
| GitHub | [https://github.com/](<https://github.com/>) |
| Hugging Face | [https://huggingface.co/](<https://huggingface.co/>) |
| GitLab | [https://gitlab.com/](<https://gitlab.com/>) |
| ModelScope | [https://modelscope.cn/](<https://modelscope.cn/>) |
| Ollama | [https://ollama.com/](<https://ollama.com/>) |
| LM Studio | [https://lmstudio.ai/](<https://lmstudio.ai/>) |
| Unsloth | [https://unsloth.ai/](<https://unsloth.ai/>) |
| vLLM | [https://vllm.ai/](<https://vllm.ai/>) |
| PyPI | [https://pypi.org/](<https://pypi.org/>) |

Monitor:

- New repositories.
- New releases.
- Version changes.
- Commit activity.
- Model uploads.
- Model card changes.
- Framework updates.
- Breaking changes.

### 6.5 Technology News

Potential sources:

- [TechCrunch](<https://techcrunch.com/>)
- [The Verge](<https://www.theverge.com/>)
- [Ars Technica](<https://arstechnica.com/>)
- [VentureBeat](<https://venturebeat.com/>)
- [MIT Technology Review](<https://www.technologyreview.com/>)
- [IEEE Spectrum](<https://spectrum.ieee.org/>)
- [InfoQ](<https://www.infoq.com/>)
- [The Register](<https://www.theregister.com/>)
- [Analytics Vidhya](<https://www.analyticsvidhya.com/>)

### 6.6 Community Sources

- [Hacker News](<https://news.ycombinator.com/>)
- [Reddit](<https://www.reddit.com/>)
- GitHub Discussions.
- Hugging Face Discussions.
- Official developer forums.

Potential Reddit communities:

- [r/LocalLLaMA](<https://www.reddit.com/r/LocalLLaMA/>)
- [r/MachineLearning](<https://www.reddit.com/r/MachineLearning/>)
- [r/LocalLLM](<https://www.reddit.com/r/LocalLLM/>)
- [r/ArtificialIntelligence](<https://www.reddit.com/r/ArtificialIntelligence/>)
- [r/StableDiffusion](<https://www.reddit.com/r/StableDiffusion/>)
- [r/LanguageTechnology](<https://www.reddit.com/r/LanguageTechnology/>)

### 6.7 YouTube Sources

Monitor technical videos, interviews, product announcements, conference presentations, and demonstrations.

Potential channels:

- OpenAI.
- Google DeepMind.
- NVIDIA.
- Microsoft Developer.
- Hugging Face.
- Andrej Karpathy.
- Yannic Kilcher.
- Two Minute Papers.
- AI Explained.
- Fireship.
- Computerphile.
- Lex Fridman.

Use the official YouTube Data API where applicable.

Collect:

- Video title.
- Channel.
- Publication date.
- Description.
- Video URL.
- Captions or transcripts where legally and technically available.
- Mentioned models and technologies.
- AI-generated summary.

### 6.8 Source Reliability

Every source should have:

- Source category.
- Collection method.
- Reliability score.
- Publication date.
- Collection timestamp.
- Original URL.
- Evidence references.

Official sources should be prioritized for release verification.

Secondary reporting and community discussions should be used as supporting evidence.

---

## 🔄 7. Data Processing Architecture

### 7.1 End-to-End Data Lifecycle

mermaid

```mermaid
flowchart TD
    A["Scheduled Collection"] --> B["Source Discovery"]
    B --> C["Fetch Original Content"]
    C --> D["Raw Document Storage"]
    D --> E["Content Validation"]
    E --> F["Normalization"]
    F --> G["Duplicate Detection"]
    G --> H["AI Classification"]
    H --> I["Entity Extraction"]
    I --> J["Release Detection"]
    J --> K["Model & Technology Extraction"]
    K --> L["Hardware Analysis"]
    L --> M["Structured Database Storage"]
    M --> N["Report Generation"]
    N --> O["Dashboard & Notifications"]
```

### 7.2 Processing Status Lifecycle

Every document must have a processing status.

| Status | Description |
| --- | --- |
| `DISCOVERED` | Document identified |
| `FETCHED` | Original content retrieved |
| `VALIDATED` | Content validated |
| `NORMALIZED` | Content converted into standard format |
| `CLASSIFIED` | Content categorized |
| `ANALYZED` | Intelligence processing completed |
| `COMPLETED` | Processing successfully finished |
| `FAILED` | Processing failed |
| `SKIPPED` | Processing intentionally skipped |
| `RETRY_PENDING` | Waiting for another attempt |

Processing must be recoverable.

A failed document must not require the entire daily workflow to restart.

### 7.3 Raw Data Preservation

Original collected content must be retained separately from processed information.

This provides:

- Reprocessing capabilities.
- Auditability.
- Source verification.
- Historical comparisons.
- AI model improvement.
- Data extraction debugging.

Raw documents should include original URLs, source identifiers, publication dates, collection timestamps, and content hashes.

Retention policies must respect third-party content restrictions.

---

## 🧩 8. Core Domain Architecture

The domain layer organizes the platform around its primary business entities.

### 8.1 Company Domain

Responsible for:

- Company information.
- Company categories.
- Official websites.
- Company products.
- Company release history.
- Company-source relationships.

### 8.2 Model Domain

Responsible for:

- AI model identity.
- Model families.
- Model versions.
- Model architectures.
- Parameter counts.
- Context windows.
- Modalities.
- Licenses.
- Model repositories.
- Model documentation.

A model family and a model version must be separate entities.

A model release may have multiple quantized variants, checkpoints, artifacts, and deployment formats.

### 8.3 Technology Domain

Responsible for:

- AI frameworks.
- Libraries.
- Inference engines.
- Agent frameworks.
- Vector databases.
- Development platforms.
- AI infrastructure.
- Technology releases.

### 8.4 Research Domain

Responsible for:

- Academic papers.
- Research organizations.
- Authors.
- Publication dates.
- Research categories.
- Model and technology references.
- Citation metadata.

### 8.5 Hardware Domain

Responsible for:

- GPU specifications.
- CPU specifications.
- AI accelerators.
- Memory capacity.
- Memory bandwidth.
- Supported precision formats.
- Architecture compatibility.
- Model hardware requirements.
- Inference estimates.

### 8.6 Intelligence Domain

Responsible for:

- Classification.
- Summarization.
- Entity extraction.
- Release detection.
- Deduplication.
- Relevance scoring.
- Version comparisons.
- AI-generated reports.

---

## 🗄️ 9. Database Architecture

### 9.1 Database Technology

PostgreSQL will be the primary relational database.

Recommended implementation:

- PostgreSQL 16 or later.
- SQLAlchemy 2.x.
- Alembic.
- UUID primary keys.
- JSONB metadata.
- TIMESTAMPTZ timestamps.
- Foreign key constraints.
- Indexed search fields.
- Transaction-based writes.

### 9.2 Logical Database Structure

| Domain | Main Tables |
| --- | --- |
| Identity | `users`, `roles`, `permissions` |
| Organizations | `companies`, `company_categories` |
| Sources | `sources`, `source_categories` |
| Collection | `collection_jobs`, `raw_documents` |
| Content | `articles`, `article_sources` |
| Models | `models`, `model_versions`, `model_specs` |
| Technologies | `technologies`, `technology_versions` |
| Research | `research_papers`, `research_authors` |
| Hardware | `hardware_devices`, `model_hardware_requirements` |
| Compatibility | `hardware_compatibility`, `quantization_formats` |
| Intelligence | `classifications`, `summaries`, `analyses` |
| Evidence | `evidence`, `evidence_sources` |
| Reporting | `reports`, `report_items` |
| Automation | `workflow_executions` |
| Operations | `audit_logs`, `notifications` |

### 9.3 Database Design Rules

- Use UUID primary keys.
- Preserve external source identifiers.
- Enforce unique constraints for external identifiers.
- Store original publication dates separately from collection dates.
- Keep raw and normalized content separate.
- Maintain historical model versions.
- Store AI processing metadata.
- Store confidence and verification status.
- Maintain source provenance.
- Index frequently searched fields.
- Use JSONB for flexible metadata, not as a replacement for relational design.
- Use migrations for all schema changes.

---

## 🧠 10. AI Intelligence Engine

### 10.1 Processing Components

| Component | Responsibility |
| --- | --- |
| Classifier | Categorize collected content |
| Entity Extractor | Identify companies, models, and technologies |
| Release Detector | Identify actual releases and updates |
| Version Extractor | Extract version identifiers |
| Summarizer | Generate concise technical summaries |
| Comparator | Compare new and historical versions |
| Deduplicator | Identify duplicate information |
| Relevance Engine | Determine industry importance |
| Evidence Validator | Link extracted facts to original sources |

### 10.2 AI Provider Abstraction

The intelligence engine must not be tightly coupled to one LLM provider.

Create a provider-independent interface supporting configurable integrations such as:

- OpenAI.
- Anthropic.
- Google Gemini.
- Local Ollama models.
- Other compatible inference APIs.

Provider selection should be configurable.

### 10.3 Structured AI Outputs

All extraction operations should produce validated structured outputs.

Example:

json

```json
{
  "document_type": "MODEL_RELEASE",
  "company": "Example AI Company",
  "model_name": "Example Model",
  "version": "1.0",
  "release_date": "2026-11-21",
  "model_type": "LLM",
  "license_type": "OPEN_WEIGHT",
  "parameter_count": "8B",
  "context_window": 128000,
  "confidence": 0.92,
  "verification_status": "NEEDS_REVIEW"
}
```

The example is illustrative.

The system must not invent missing specifications. Unknown values should remain `null` or explicitly marked as unknown.

### 10.4 Processing Versioning

Maintain:

- Provider identifier.
- Model identifier.
- Prompt version.
- Extraction schema version.
- Processing timestamp.
- Token consumption.
- Processing duration.
- Validation status.

This allows historical analysis to be reproduced and compared.

---

## 🖥️ 11. Hardware Intelligence Engine

Hardware intelligence is one of the core differentiating features of LLM Radar.

### 11.1 Hardware Analysis Inputs

- Parameter count.
- Model architecture.
- Number of active parameters.
- Precision.
- Quantization format.
- Context length.
- Batch size.
- Concurrent users.
- Inference framework.
- GPU memory.
- System memory.

### 11.2 Memory Estimation

Approximate model weight memory:

text

```text
Weight Memory =
Parameter Count × Bytes Per Parameter
```

Approximate bytes per parameter:

| Format | Approximate Bytes |
| --- | --- |
| FP32 | 4 |
| FP16 | 2 |
| BF16 | 2 |
| FP8 | 1 |
| INT8 | 1 |
| INT4 | 0.5 |

Actual memory usage may be higher due to metadata, scales, runtime overhead, padding, and architecture-specific implementation.

Total GPU memory estimation must account for:

text

```text
Total VRAM =
    Model Weights
  + KV Cache
  + Runtime Overhead
  + Activation Memory
  + Additional Workspace
```

### 11.3 GPU Compatibility

Initial hardware coverage:

- NVIDIA GeForce RTX.
- NVIDIA RTX Professional.
- NVIDIA A100.
- NVIDIA H100.
- NVIDIA H200.
- NVIDIA B200.
- AMD Radeon.
- AMD Instinct.
- Apple Silicon.
- Other AI accelerators.

Compatibility must consider framework, driver, architecture, precision, and kernel support rather than relying on GPU memory capacity alone.

### 11.4 Quantization Support

Analyze:

- FP32.
- FP16.
- BF16.
- FP8.
- INT8.
- INT4.
- GGUF.
- GPTQ.
- AWQ.
- EXL2.

### 11.5 Hardware Estimation Classification

Every hardware requirement must be classified as:

| Classification | Description |
| --- | --- |
| `OFFICIAL` | Published by model provider |
| `VERIFIED` | Independently tested |
| `CALCULATED` | Derived from technical specifications |
| `COMMUNITY_REPORTED` | Reported by users |
| `AI_ESTIMATED` | Generated through AI analysis |

### 11.6 Hardware Advisor

Users should be able to select their hardware and discover:

- Which models can run locally.
- Which models require quantization.
- Which models require multiple GPUs.
- Which models support CPU inference.
- Expected memory utilization.
- Estimated inference performance.
- Approximate cloud deployment cost.

All estimates must expose their assumptions and confidence levels.

---

## ⚙️ 12. Backend Architecture

### 12.1 Technology Stack

- Python 3.12+.
- FastAPI.
- SQLAlchemy 2.x.
- Pydantic.
- Alembic.
- PostgreSQL.
- HTTPX.
- Pytest.

### 12.2 Backend Module Structure

text

```text
backend/
├── app/
│   ├── api/
│   │   ├── routes/
│   │   └── dependencies.py
│   │
│   ├── core/
│   │   ├── config.py
│   │   ├── security.py
│   │   ├── logging.py
│   │   └── exceptions.py
│   │
│   ├── db/
│   │   ├── base.py
│   │   └── session.py
│   │
│   ├── domains/
│   │   ├── identity/
│   │   ├── companies/
│   │   ├── sources/
│   │   ├── collection/
│   │   ├── models/
│   │   ├── technologies/
│   │   ├── research/
│   │   ├── intelligence/
│   │   ├── hardware/
│   │   └── reporting/
│   │
│   ├── collectors/
│   │   ├── base.py
│   │   ├── rss/
│   │   ├── company/
│   │   ├── github/
│   │   ├── huggingface/
│   │   ├── arxiv/
│   │   ├── youtube/
│   │   ├── reddit/
│   │   └── hackernews/
│   │
│   ├── services/
│   ├── workers/
│   └── main.py
│
├── alembic/
├── tests/
├── requirements.txt
└── Dockerfile
```

### 12.3 API Architecture

Suggested API groups:

text

```text
/api/v1/auth
/api/v1/users
/api/v1/companies
/api/v1/sources
/api/v1/collection
/api/v1/articles
/api/v1/models
/api/v1/model-versions
/api/v1/technologies
/api/v1/research
/api/v1/hardware
/api/v1/compatibility
/api/v1/intelligence
/api/v1/reports
/api/v1/notifications
/api/v1/health
```

The API must support:

- Pagination.
- Filtering.
- Sorting.
- Search.
- Validation.
- Consistent error responses.
- Authentication.
- Authorization.
- Versioning.

---

## 🔄 13. Automation Architecture

### 13.1 n8n Responsibilities

n8n is the external workflow orchestration layer.

It will not contain the core business logic.

Primary workflows:

- Daily collection workflow.
- Failed job recovery workflow.
- AI processing workflow.
- Daily report workflow.
- Weekly report workflow.
- Monthly report workflow.
- Notification workflow.

### 13.2 Daily Workflow

**Default schedule:** `00:00 Asia/Dhaka`

mermaid

```mermaid
flowchart TD
    A["Daily Schedule"] --> B["Start Collection Job"]
    B --> C["Collect Active Sources"]
    C --> D["Normalize Documents"]
    D --> E["Detect Duplicates"]
    E --> F["Run Intelligence Processing"]
    F --> G["Extract Model & Technology Data"]
    G --> H["Run Hardware Analysis"]
    H --> I["Persist Results"]
    I --> J["Generate Daily Report"]
    J --> K["Send Notifications"]
    K --> L["Record Execution Status"]
```

### 13.3 Reliability Requirements

- Idempotent API operations.
- Execution identifiers.
- Retry with exponential backoff.
- Per-source error tracking.
- Failed-job recovery.
- Rate limiting.
- Workflow monitoring.
- Execution history.
- Duplicate prevention.

The collection pipeline must support manual execution independently of n8n.

---

## 🎨 14. Frontend Architecture

### 14.1 Technology

- Next.js.
- React.
- TypeScript.
- Tailwind CSS.
- API-driven data access.

### 14.2 Main Application Modules

text

```text
frontend/
├── app/
│   ├── dashboard/
│   ├── daily/
│   ├── weekly/
│   ├── monthly/
│   ├── models/
│   ├── companies/
│   ├── technologies/
│   ├── research/
│   ├── hardware/
│   ├── sources/
│   └── settings/
│
├── components/
├── services/
├── hooks/
├── types/
└── public/
```

### 14.3 Dashboard Requirements

- Latest AI developments.
- New model releases.
- Company announcements.
- Technology updates.
- Open-source releases.
- Research papers.
- Hardware developments.
- Trending technologies.
- Daily intelligence summaries.

### 14.4 Reporting Requirements

**Daily Reports:**

- Newly detected releases.
- Important announcements.
- Research highlights.
- New model specifications.

**Weekly Reports:**

- Industry trends.
- Company comparisons.
- Major releases.
- Technology developments.

**Monthly Reports:**

- AI ecosystem analysis.
- Company activity.
- Model release statistics.
- Emerging technology trends.
- Hardware developments.

---

## 🔐 15. Security Architecture

Security must be considered throughout the system lifecycle.

Requirements:

- JWT-based authentication.
- Password hashing.
- Role-based access control.
- API input validation.
- Secure secret management.
- Database access restrictions.
- API rate limiting.
- HTTPS in production.
- Audit logging.
- Container security.
- Database backup and recovery.
- Dependency vulnerability scanning.

> **Important:** External source content must be treated as untrusted data.

Collected articles, web pages, transcripts, and model cards must never be treated as executable instructions by the AI processing engine.

---

## 📊 16. Observability and Reliability

The platform must provide visibility into all background activities.

Track:

- Collection execution status.
- Source response times.
- API failures.
- Rate-limit events.
- Processing failures.
- AI provider usage.
- Token consumption.
- Processing duration.
- Duplicate detection statistics.
- Report generation status.
- Database health.

Each collection and processing operation should have a traceable execution ID.

Logs should be structured and suitable for centralized monitoring in future deployments.

---

## 🐳 17. Deployment Architecture

### 17.1 Initial Infrastructure

Docker Compose will be used for initial deployment.

mermaid

```mermaid
flowchart TB
    USER["User Browser"]

    subgraph HOST["Docker Host"]
        FRONT["Next.js Container"]
        BACK["FastAPI Container"]
        DB[("PostgreSQL Container")]
        N8N["n8n Container"]
        WORKER["Background Worker"]
    end

    USER --> FRONT
    FRONT --> BACK
    N8N --> BACK
    BACK --> DB
    WORKER --> DB
    BACK --> WORKER
```

### 17.2 Infrastructure Components

| Component | Responsibility |
| --- | --- |
| Next.js | User interface |
| FastAPI | Application API |
| PostgreSQL | Primary database |
| n8n | Workflow orchestration |
| Background Worker | Collection and processing |
| Docker | Container management |

Redis and a dedicated job queue may be introduced when workload volume justifies them.

### 17.3 Environment Configuration

All environment-specific settings must be externalized.

Example:

env

```env
PROJECT_NAME=LLM Radar
ENVIRONMENT=development

TIMEZONE=Asia/Dhaka

DATABASE_HOST=postgres
DATABASE_PORT=5432
DATABASE_NAME=llm_radar
DATABASE_USER=llm_radar
DATABASE_PASSWORD=change_me

API_SECRET_KEY=change_me

GITHUB_TOKEN=
HUGGINGFACE_TOKEN=
YOUTUBE_API_KEY=
REDDIT_CLIENT_ID=
REDDIT_CLIENT_SECRET=

OPENAI_API_KEY=
ANTHROPIC_API_KEY=
GOOGLE_API_KEY=
```

Secrets must never be committed to version control.

---

## 📁 18. Project Structure

text

```text
llm-radar/
│
├── backend/
│   ├── app/
│   ├── alembic/
│   ├── tests/
│   ├── requirements.txt
│   └── Dockerfile
│
├── frontend/
│   ├── app/
│   ├── components/
│   ├── services/
│   └── Dockerfile
│
├── n8n/
│   └── workflows/
│       ├── daily_ai_intelligence.json
│       ├── weekly_report.json
│       └── monthly_report.json
│
├── database/
│   ├── init/
│   └── seeds/
│
├── scripts/
│
├── docs/
│   ├── adr/
│   │   ├── README.md
│   │   ├── ADR-0001-modular-monolith.md
│   │   ├── ADR-0002-postgresql.md
│   │   ├── ADR-0003-fastapi-backend.md
│   │   ├── ADR-0004-n8n-orchestration.md
│   │   ├── ADR-0005-background-processing.md
│   │   ├── ADR-0006-source-registry.md
│   │   ├── ADR-0007-raw-data-preservation.md
│   │   ├── ADR-0008-ai-provider-abstraction.md
│   │   ├── ADR-0009-hardware-estimation.md
│   │   ├── ADR-0010-nextjs-frontend.md
│   │   ├── ADR-0011-docker-deployment.md
│   │   ├── ADR-0012-api-versioning.md
│   │   ├── ADR-0013-data-provenance.md
│   │   ├── ADR-0014-authentication.md
│   │   └── ADR-0015-timezone-scheduling.md
│   │
│   ├── architecture/
│   │   ├── overview.md
│   │   ├── system-context.md
│   │   ├── data-flow.md
│   │   └── deployment.md
│   │
│   ├── database/
│   │   └── database-design.md
│   │
│   ├── api/
│   │   └── api-design.md
│   │
│   └── development-roadmap.md
│
├── docker-compose.yml
├── .env.example
├── .gitignore
├── LICENSE
└── README.md
```

---

## 🔧 19. Technology Stack

| Layer | Technology |
| --- | --- |
| Programming Language | Python 3.12+ |
| Backend | FastAPI |
| ORM | SQLAlchemy 2.x |
| Validation | Pydantic |
| Database | PostgreSQL 16+ |
| Database Migrations | Alembic |
| Automation | n8n |
| Frontend | Next.js |
| UI | React + TypeScript |
| Styling | Tailwind CSS |
| Authentication | JWT |
| HTTP Client | HTTPX |
| RSS Collection | feedparser |
| GitHub Collection | GitHub REST API |
| Hugging Face | Hugging Face Hub API |
| Academic Research | arXiv API |
| Video Collection | YouTube Data API |
| Community Collection | Reddit / Hacker News APIs |
| AI Processing | Configurable LLM providers |
| Testing | Pytest |
| Containerization | Docker |
| Deployment | Docker Compose |

Additional infrastructure such as Redis, distributed workers, pgvector, and dedicated search services can be introduced when justified by actual requirements.

---

## 🚀 20. Installation and Setup

### 20.1 Prerequisites

Install:

- Docker.
- Docker Compose.
- Git.
- Python 3.12+ for local backend development.

### 20.2 Clone Repository

bash

```bash
git clone https://github.com/YOUR_USERNAME/llm-radar.git

cd llm-radar
```

### 20.3 Environment Configuration

Create an environment file:

bash

```bash
cp .env.example .env
```

Configure the required environment variables.

**Example:**

env

```env
PROJECT_NAME=LLM Radar
ENVIRONMENT=development

TIMEZONE=Asia/Dhaka

DATABASE_HOST=postgres
DATABASE_PORT=5432
DATABASE_NAME=llm_radar
DATABASE_USER=llm_radar
DATABASE_PASSWORD=change_this_password

DATABASE_URL=postgresql+psycopg://llm_radar:change_this_password@postgres:5432/llm_radar

API_SECRET_KEY=replace_with_secure_random_secret

GITHUB_TOKEN=
HUGGINGFACE_TOKEN=
YOUTUBE_API_KEY=

REDDIT_CLIENT_ID=
REDDIT_CLIENT_SECRET=

OPENAI_API_KEY=
ANTHROPIC_API_KEY=
GOOGLE_API_KEY=
```

### 20.4 Start Docker Environment

bash

```bash
docker compose up -d --build
```

### 20.5 Check Running Containers

bash

```bash
docker compose ps
```

### 20.6 Run Database Migrations

bash

```bash
docker compose exec backend alembic upgrade head
```

### 20.7 View Logs

bash

```bash
docker compose logs -f
```

> **Implementation note:** These commands describe the intended installation workflow. The corresponding application files and services will be implemented during the development phases.

---

## 🔌 21. API Architecture

All backend APIs will use the `/api/v1` prefix.

### 21.1 API Groups

| API | Purpose |
| --- | --- |
| `/api/v1/auth` | Authentication |
| `/api/v1/users` | User management |
| `/api/v1/companies` | Company directory |
| `/api/v1/sources` | Source management |
| `/api/v1/collection` | Collection execution |
| `/api/v1/articles` | Collected content |
| `/api/v1/models` | Model catalog |
| `/api/v1/model-versions` | Model version history |
| `/api/v1/technologies` | Technology catalog |
| `/api/v1/research` | Research papers |
| `/api/v1/hardware` | Hardware database |
| `/api/v1/compatibility` | Model compatibility |
| `/api/v1/intelligence` | AI analysis |
| `/api/v1/reports` | Intelligence reports |
| `/api/v1/notifications` | Notifications |
| `/api/v1/health` | Health checks |

### 21.2 API Standards

- RESTful resource design.
- Pydantic validation.
- Pagination.
- Filtering.
- Sorting.
- Consistent error responses.
- Authentication.
- Authorization.
- OpenAPI documentation.
- API versioning.

---

## 📈 22. Reporting and Dashboard

### 22.1 Dashboard Metrics

- Total monitored sources.
- Total collected documents.
- New AI models this week.
- New technology releases this month.
- Companies with recent announcements.
- New open-source models.
- New research papers.
- Trending AI technologies.
- New GPU and hardware releases.

### 22.2 Daily Report

- New AI model releases.
- Technology releases.
- Company announcements.
- GitHub releases.
- New research papers.
- Important technical videos.
- Important industry news.
- Model version changes.
- Hardware announcements.

### 22.3 Weekly Report

- Important AI developments.
- New model families.
- Company release comparisons.
- Trending open-source projects.
- Important research developments.
- New AI frameworks.
- Hardware developments.

### 22.4 Monthly Report

- Major AI industry developments.
- Company release statistics.
- New models by company.
- Open-source versus proprietary releases.
- Emerging technologies.
- Most active AI companies.
- Trending GitHub projects.
- Hardware developments.
- Significant research developments.

---

## 🗺️ 23. Development Roadmap

Development will follow eight structured phases.

### Development Status

### Part 1 — Project Foundation

- Docker configuration.
- PostgreSQL database.
- Environment variables.
- SQLAlchemy foundation.
- Alembic migrations.
- Initial database schema.
- Configuration management.
- Health checks.
- Project documentation.

### Part 2 — Python Backend

- FastAPI application.
- Domain modules.
- SQLAlchemy models.
- API endpoints.
- Authentication.
- Logging.
- Error handling.

### Part 3 — Data Collectors

- RSS.
- Official company websites.
- GitHub.
- Hugging Face.
- arXiv.
- YouTube.
- Reddit.
- Hacker News.

### Part 4 — AI Intelligence Engine

- Classification.
- Summarization.
- Release detection.
- Entity extraction.
- Model extraction.
- Deduplication.
- Historical comparison.

### Part 5 — Hardware Intelligence

- VRAM estimation.
- RAM estimation.
- GPU compatibility.
- Quantization.
- Inference cost estimation.

### Part 6 — n8n Automation

- Daily scheduler.
- Importable workflow JSON.
- API integration.
- Retries.
- Notifications.
- Execution monitoring.

### Part 7 — Web Application

- Dashboard.
- Daily, weekly, and monthly reports.
- Model directory.
- Company directory.
- Technology directory.
- Hardware advisor.
- Source management.

### Part 8 — Testing and Deployment

- Automated tests.
- Security review.
- Performance testing.
- Database backups.
- Production deployment.
- Monitoring.

---

## 📋 24. Non-Functional Requirements

| Requirement | Target |
| --- | --- |
| Extensibility | New sources without changing core architecture |
| Reliability | Recoverable collection and processing |
| Data Integrity | Transactional database operations |
| Traceability | Original evidence for intelligence records |
| Security | Authenticated and authorized APIs |
| Maintainability | Modular code and documented interfaces |
| Scalability | Independent background processing |
| Observability | Execution and error tracking |
| Reproducibility | Versioned analysis and migrations |
| Portability | Docker-based deployment |

Performance targets will be established after measuring actual collection volume and processing workloads.

---

## 🔮 25. Future Enhancements

Potential future capabilities:

- AI model benchmarking database.
- Automatic model comparison.
- Local GPU hardware inventory.
- Model deployment recommendations.
- AI model leaderboards.
- AI technology trend analysis.
- Company innovation tracking.
- AI startup monitoring.
- Automatic release notifications.
- Email and Telegram notifications.
- Slack and Discord integration.
- Model API price comparison.
- Cloud GPU price comparison.
- Local LLM recommendation engine.
- Model download and deployment guides.
- Automatic technical research reports.
- Semantic search.
- Natural-language questions about the AI ecosystem.
- pgvector-based similarity search.
- Independent collector and intelligence workers.
- Advanced AI research assistant.

---

## 🤝 26. Contribution Guidelines

Contributions are welcome.

Potential contribution areas:

- New AI information sources.
- Company release monitoring.
- Model metadata extraction.
- Hardware compatibility data.
- Model benchmarking.
- AI technology classification.
- Collector integrations.
- Dashboard improvements.
- Documentation and testing.

### 26.1 Contribution Standards

- Follow the existing modular architecture.
- Write readable and maintainable code.
- Include tests for important business logic.
- Update documentation.
- Add an ADR for significant architectural changes.
- Never commit secrets or credentials.
- Preserve source attribution.
- Follow existing database migration standards.

---

## 📄 27. License

This project is intended to use the **MIT License** unless a different license is selected before the first public release.

Third-party information remains subject to its respective copyright, ownership, licensing, and usage restrictions.

The system must maintain source attribution and comply with applicable API and content usage policies.

---

## ⭐ 28. Project Mission

LLM Radar aims to become a comprehensive intelligence platform for understanding the global AI ecosystem.

It will connect information from companies, researchers, developers, open-source communities, and technology providers into one structured intelligence system.

The goal is not simply to collect AI news.

The goal is to understand:

- What has changed?
- Why does it matter?
- What technology is involved?
- What are its capabilities?
- What hardware is required?
- How does it compare with previous developments?
- How is the AI ecosystem evolving?

### One platform. One intelligence layer. A continuously updated view of the AI ecosystem.

---

## 📌 Project Information

| Attribute | Value |
| --- | --- |
| **Project** | LLM Radar |
| **Category** | AI Intelligence / Technology Monitoring |
| **Architecture** | Modular Monolith / Event-Driven Processing |
| **Backend** | Python / FastAPI |
| **Database** | PostgreSQL |
| **ORM** | SQLAlchemy |
| **Migrations** | Alembic |
| **Automation** | n8n |
| **Frontend** | Next.js / React |
| **Infrastructure** | Docker / Docker Compose |
| **API** | REST / OpenAPI |
| **Scheduling** | Daily at 00:00 |
| **Default Timezone** | Asia/Dhaka |
| **License** | MIT (intended) |

---

<p align="center">
<strong>🚀 LLM Radar</strong>
<br>
Discover. Monitor. Analyze. Compare. Understand.
<br><br>
<i>Building a continuously updated intelligence layer for the global AI ecosystem.</i>
</p>

