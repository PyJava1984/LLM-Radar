# ADR-0009: Hardware Estimation Architecture

## Status

**Accepted**

## Date

2026-11-21

---

## 1\. Context

Users need to understand which hardware configurations can run specific AI models.

Model memory requirements vary depending on several factors, including:

- Model precision.
- Quantization method.
- Context length.
- Batch size.
- Model architecture.
- Inference runtime.

A reliable hardware intelligence system is required to estimate memory requirements, recommend suitable GPUs, and distinguish verified hardware compatibility from calculated or inferred results.

## 2\. Decision

Implement a dedicated **Hardware Intelligence Domain**.

The following decisions have been made:

- Hardware estimation must be implemented as a separate domain within the application architecture.
- Official hardware requirements must be distinguished from calculated estimates.
- Verified test results, community reports, and AI-generated approximations must be tracked separately.
- Hardware recommendations must consider model configuration and inference parameters.
- Estimation assumptions and confidence levels must be recorded to ensure transparency and reproducibility.

## 3\. Alternatives Considered

The following alternatives were evaluated:

| Alternative | Description |
| --- | --- |
| Store a Single VRAM Number Per Model | Maintain only one VRAM requirement value for each AI model. |
| Use AI-Generated Estimates Exclusively | Rely entirely on AI-generated hardware memory estimates. |
| Rely Exclusively on Community Benchmarks | Use community-reported hardware benchmarks as the only source of compatibility information. |

## 4\. Consequences

### Positive

- More transparent and explainable hardware estimates.
- Better GPU recommendations based on model configurations.
- Support for historical estimation improvements.
- Clear distinction between verified facts, calculated estimates, and assumptions.
- Improved hardware compatibility analysis.
- Greater flexibility when supporting new model architectures and inference runtimes.

### Negative

- Requires detailed hardware specifications and documented calculation methodologies.
- Exact runtime compatibility may require real-world testing.
- Estimation accuracy depends on the quality and completeness of model and hardware metadata.
- Multiple estimation variables increase implementation complexity.

## 5\. Implementation

The following implementation requirements must be followed:

- Record model precision and quantization settings.
- Record the configured context length.
- Record the inference batch size.
- Account for KV cache memory requirements.
- Track GPU architecture and hardware specifications.
- Record the inference framework and runtime.
- Store estimation assumptions and calculation parameters.
- Maintain confidence indicators for calculated estimates.
- Distinguish official requirements, calculated estimates, verified tests, community reports, and AI-generated approximations.
- Preserve historical estimation records to support future methodology improvements.
- Avoid presenting calculated estimates as guaranteed hardware compatibility.

### 5.1. Hardware Estimation Parameters

| Parameter | Description |
| --- | --- |
| Model Architecture | Architecture of the AI model. |
| Precision | Numerical precision used for model weights and computation. |
| Quantization | Quantization method and bit width applied to the model. |
| Context Length | Maximum configured input and output context length. |
| Batch Size | Number of input sequences processed together. |
| KV Cache | Memory required for key-value attention caching. |
| GPU Architecture | GPU architecture and supported hardware capabilities. |
| Inference Framework | Framework used to execute the model. |
| Confidence | Confidence indicator associated with the estimation. |

### 5.2. Hardware Intelligence Data Categories

| Category | Description |
| --- | --- |
| Official Requirements | Hardware requirements published by the original model or hardware provider. |
| Calculated Estimates | Memory and hardware requirements derived using documented estimation methodologies. |
| Verified Tests | Hardware compatibility and performance results confirmed through actual testing. |
| Community Reports | Hardware usage and compatibility information reported by the community. |
| AI-Generated Approximations | Hardware estimates generated using AI-based reasoning or approximation. |

### 5.3. Estimation Guidelines

- Hardware estimates must consider model configuration rather than relying on a single fixed VRAM value.
- KV cache requirements must be considered when estimating inference memory.
- GPU architecture and inference runtime must be included in compatibility analysis.
- Estimation assumptions must be documented and traceable.
- Confidence indicators must not be treated as proof of actual hardware compatibility.
- Verified test results must remain distinguishable from theoretical calculations.
- Estimation methodologies should be continuously improved using historical test results and additional evidence.

## 6\. Related ADRs

- **ADR-0002**
- **ADR-0007**
- **ADR-0013**
