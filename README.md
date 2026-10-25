# AI Research Portfolio

Public personal projects exploring AI, model interpretability, systems programming, high performance computing, and datasets from the physical world.

**Current status:** the portfolio structure and initial project briefs are published. Implementations, datasets, and experimental results will be added as the work progresses. This repository is an index and a set of containers for independent projects.

## Research areas

| Container | Scope |
| --- | --- |
| [Interpretability](Interpretability/) | Understand and test how models work. [Mechanistic Interpretability](<Interpretability/Mechanistic Interpretability/>) is the first dedicated subfolder. |
| [AI Systems and HPC](<AI Systems and HPC/>) | Build useful tools with Rust, GPU computing, PTX, SASS analysis, and measured performance. |
| [Datasets](Datasets/) | Create, clean, annotate, and document datasets, including physical measurements. |
| [Education](Education/) | Explain AI and machine learning through interactive visual lessons. |

## Projects

| Project | Container | Status |
| --- | --- | --- |
| [Entity Tracking Circuits](https://github.com/AG4MA/entity-tracking-circuits) | Interpretability / Mechanistic Interpretability | Project definition published |
| [Qwen Behavior Lab](https://github.com/AG4MA/qwen-behavior-lab) | Interpretability / Mechanistic Interpretability | Neuron Explorer integrated; experiments pending |
| [Exact Vector Search](https://github.com/AG4MA/exact-vector-search) | AI Systems and HPC | Project definition published |
| [Physical Signal Anomaly Detection](https://github.com/AG4MA/physical-signal-anomaly-detection) | AI Systems and HPC | Project definition published |
| [Improving LLM Performance on GPUs Through Kernel Optimization](https://github.com/AG4MA/llm-gpu-kernel-optimization) | AI Systems and HPC | Project definition published |
| [Interactive AI and Machine Learning](Education/interactive-ai-and-ml/) | Education | Idea saved for future development |

Entity Tracking Circuits will implement a small Transformer from scratch, train it on DGX Spark, run inference, and investigate how entity tracking mechanisms emerge across training checkpoints.

Qwen Behavior Lab includes a pinned Neuron Explorer submodule to study how targeted activation steering and ablation affect Qwen's behavior.

Exact Vector Search is a standalone exploration of exhaustive nearest neighbor search with a Rust CPU baseline and a planned PTX GPU implementation.

Physical Signal Anomaly Detection connects physical recordings, model evaluation, interpretability experiments, and a possible Rust and PTX performance study.

Improving LLM Performance on GPUs Through Kernel Optimization will profile an LLM inference workload, optimize one measured GPU bottleneck, and evaluate its effect on total inference performance. Rust is a candidate for the host implementation.

## How this portfolio is organized

The areas are containers. Each implemented project has its own public repository, documentation, and history. This index links to those repositories instead of duplicating their files. Future project ideas can begin as briefs inside their container.

Empty folders use a `.gitkeep` placeholder so that their structure is visible on GitHub. These placeholders are not implementations.

Projects will report reproducible methods, correctness checks, measurements, unsuccessful experiments, and limitations. Planned work is distinguished from completed work.
