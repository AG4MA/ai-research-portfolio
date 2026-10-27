# Open GPU Computing in Rust

**Status:** project brief. No implementation, submitted contribution or portability result yet.

Contribute to open source GPU computing tools so AI workloads can run across hardware vendors. Rust is the implementation focus. Success means a useful upstream change with reproducible correctness evidence.

## First contribution

Start by evaluating [CubeCL](https://github.com/tracel-ai/cubecl), which provides Rust compute kernels and multiple execution backends. Select one small, reproducible issue in a reduction or softmax workload after checking its current contribution guide and tests.

1. Pin an upstream revision and reproduce the issue or missing test.
2. Build a CPU reference and check the relevant GPU path on the available DGX Spark.
3. Implement one focused correction and a meaningful regression test.
4. Prepare a small upstream pull request with the reproduction and measured outcome.

Additional hardware results require actual access to that hardware or verified upstream CI. A CPU and NVIDIA run alone does not demonstrate AMD, Intel or Ascend support. Confirm the selected toolchain and backend on Spark before promising that configuration.

## Two different approaches

| Approach | Candidate | Intended result |
| --- | --- | --- |
| Write portable compute kernels | [CubeCL](https://github.com/tracel-ai/cubecl) | Reuse kernel logic through different backends |
| Run existing CUDA applications elsewhere | [ZLUDA](https://github.com/vosen/ZLUDA) | Compatibility with supported CUDA interfaces on supported non-NVIDIA hardware |

CubeCL is the first candidate for this project. ZLUDA remains a distinct option if the work shifts toward CUDA compatibility, PTX translation or runtime behavior. Its documented hardware support must be checked against the specific target device.

[rust-gpu](https://github.com/Rust-GPU/rust-gpu) targets SPIR-V graphics and compute shaders. [NVIDIA CUDA Rust](https://nvidia.github.io/cuda-rust/) supports Rust host code and kernels within CUDA. Neither should be presented as a universal CUDA replacement; writing Rust does not itself remove CUDA dependencies.

## Scope and evidence

Keep independent CPU checks, small upstream changes, explicit unsupported cases and reproducible measurements. Begin with correctness; optimize only a measured bottleneck. Do not claim universal binary compatibility or equal performance across devices.

The existing LLM kernel optimization project studies performance on a specific GPU. This project studies portability and contributions to shared infrastructure. They may reuse workloads without claiming the same outcome.

## Sources

Checked on 2026-10-27: the linked upstream repositories, [ZLUDA hardware FAQ](https://zluda.readthedocs.io/latest/faq.html) and [CubeCL contribution guide](https://github.com/tracel-ai/cubecl/blob/main/CONTRIBUTING.md). Recheck versions, issue availability and hardware support before implementation.
