# Open Ascend Backend in Rust

**Status:** project brief. No implementation or verified Ascend execution yet.

Build an open source Rust backend that lets a small AI workload execute on Huawei Ascend through CANN behind a portable application interface. Ascend already operates without CUDA. The goal is to make software that currently depends on CUDA easier to move between accelerators.

## First working slice

Start with a narrow runtime integration, not a complete compiler:

1. Define a small tensor operation interface and a CPU reference.
2. Wrap the selected CANN runtime API for device initialization, owned buffers, streams, memory copies and synchronization.
3. Execute one supported operation, initially a candidate such as elementwise addition, and compare the output with the CPU reference.
4. Verify resource cleanup, error propagation and synchronization on real Ascend hardware.

Use Rust ownership and RAII where the native API permits it. Keep necessary unsafe FFI code small and reviewable. The accelerator kernel can initially use an existing CANN operation; a Rust host wrapper does not imply that its kernel is written in Rust.

Keep the portable core independent from the vendor backend. Publish a capability table and reject unsupported operations explicitly. Expand toward more operators or compiler integration only after the first execution is verified.

## Existing projects to evaluate

| Project | Relevant role |
| --- | --- |
| [Triton-Ascend](https://github.com/triton-lang/triton-ascend) | Existing Triton compiler and kernel work for Ascend; an upstream contribution option, not primarily a Rust project |
| [TorchNPU](https://github.com/Ascend/pytorch) | PyTorch integration, operators and runtime behavior on Ascend |
| [hiai-rs](https://github.com/rustnn/hiai-rs) | Experimental HiAI/CANN DDK integration for offline model inference on OpenHarmony |
| [CANN runtime source](https://github.com/hicann/runtime/blob/master/README_en.md) | Runtime architecture and available device, memory, stream and event interfaces |

The documented scope of hiai-rs is not a general Linux Ascend kernel runtime. Evaluate the target operating system, APIs and existing bindings before choosing a dependency. Do not assume arbitrary Rust, WebGPU, PTX or SASS code can execute on Ascend unchanged.

## Openness and dependencies

CANN has public source components. The linked runtime's [CANN Open Software License Agreement 2.0](https://github.com/hicann/runtime/blob/master/LICENSE) contains restrictions tying use and derivatives to specified Huawei systems. Public source availability does not establish unrestricted portability of the entire stack.

Author the portable Rust core independently and keep vendor dependencies separate. Record the exact licenses, SDK, driver and firmware requirements of the components actually selected. A wrapper cannot by itself remove those platform dependencies.

## Hardware and validation

The currently verified lab accelerator is DGX Spark. It can support the NVIDIA comparison path and CPU reference work, but it cannot validate Ascend execution. Without confirmed Ascend access, only interface design, compilation checks and clearly labeled mock tests are possible. Do not report NPU compatibility or performance from mocks.

The first delivery should include one working operation, CPU agreement, repeatable setup and measured resource behavior. Full CUDA compatibility, replacement firmware and a universal compiler are outside the initial milestone.

Sources checked on 2026-10-27. Recheck the selected versions and device compatibility before implementation.
