# Real-Time GPU-Based SPH Fluid Simulation Using Vulkan and OpenGL Compute Shaders

[![Download PDF](https://img.shields.io/badge/Thesis-Download%20PDF-1A4B84?style=flat-square&logo=adobeacrobatreader&logoColor=white)](https://github.com/multiprecision/undergraduate_thesis/raw/master/undergraduate_thesis.pdf)
[![IEEE Paper](https://img.shields.io/badge/IEEE%20ICST%202018-Published%20Paper-00629B?style=flat-square&logo=ieee&logoColor=white)](https://ieeexplore.ieee.org/document/8528699)
[![Vulkan Implementation](https://img.shields.io/badge/Code-Vulkan-AC162C?style=flat-square&logo=vulkan&logoColor=white)](https://github.com/multiprecision/sph_vulkan)
[![OpenGL Implementation](https://img.shields.io/badge/Code-OpenGL%204.6-5586A4?style=flat-square&logo=opengl&logoColor=white)](https://github.com/multiprecision/sph_opengl)

Undergraduate thesis for the Bachelor of Informatics at Universitas Pelita Harapan (January 2018), investigating the performance and architectural trade-offs of Vulkan versus OpenGL 4.6 compute shaders for real-time Smoothed Particle Hydrodynamics (SPH) fluid simulation. A condensed version of this research was published at the 2018 4th International Conference on Science and Technology (ICST) by IEEE.

---

## Overview

Unlike CPUs that rely on high clock frequencies for serial throughput, Graphics Processing Units (GPUs) leverage massively parallel streaming multiprocessors (SMs) to achieve faster execution at lower power consumption for data-parallel workloads. Because the Smoothed Particle Hydrodynamics (SPH) fluid simulation method is inherently parallelizable and scales well with particle count, it is well-suited for GPU compute pipelines.

This thesis designs a parallel SPH algorithm written in GLSL (OpenGL Shading Language) compute shaders, compiled to SPIR-V (Standard Portable Intermediate Representation), and executed across both Vulkan and OpenGL 4.6 for a direct, apples-to-apples real-time GPU performance comparison.

---

## Key Findings

* Unified Shader Pipeline: Compiling shared GLSL compute shaders into SPIR-V enabled identical simulation math across both graphics APIs while isolating API-level overhead.
* Optimal Work-Group Size: Empirical profiling identified a compute work-group size of 128 as optimal across the tested workloads.
* Vulkan vs. OpenGL Scaling: The Vulkan compute pipeline outperformed OpenGL 4.6 at 30,000 or more particles, demonstrating lower driver overhead as parallel workload intensity increases.

---

## Verification Test Cases

Both implementations were visually verified at room temperature using two standard fluid-dynamics benchmarks:

1. Water cube drop. Dropping a suspended cube of water into an enclosed box to verify gravitational acceleration, impact dispersion, and boundary collision handling.
2. Dam break. Releasing a stationary fluid column inside a closed channel to evaluate wave propagation, pressure forces, and turbulent splashing.

---

## Companion Source Code

The C++ and GLSL compute shader implementations benchmarked in this thesis are maintained in separate repositories:

| Repository | Graphics/Compute API |
| :--- | :--- |
| [sph_vulkan](https://github.com/multiprecision/sph_vulkan) | Vulkan |
| [sph_opengl](https://github.com/multiprecision/sph_opengl) | OpenGL 4.6 |

---

## Thesis PDF

Download the full thesis directly from [`undergraduate_thesis.pdf`](https://github.com/multiprecision/undergraduate_thesis/raw/master/undergraduate_thesis.pdf).

---

## Citation

If you reference this thesis or the accompanying IEEE ICST 2018 conference paper, please cite:

```bibtex
@inproceedings{gunadi2018sph,
  author    = {Samuel Ivan Gunadi},
  title     = {Real-Time GPU-Based SPH Fluid Simulation Using Vulkan and OpenGL Compute Shaders},
  booktitle = {2018 4th International Conference on Science and Technology (ICST)},
  year      = {2018},
  month     = nov,
  publisher = {IEEE},
  url       = {[https://ieeexplore.ieee.org/document/8528699](https://ieeexplore.ieee.org/document/8528699)}
}
