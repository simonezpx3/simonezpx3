# simonezpx3 — Local-First AI, 3D V-Cache & Omarchy Linux Engineering

[![OS: Omarchy Linux](https://img.shields.io/badge/OS-Omarchy%20%2F%20Arch%20Linux-1793d1.svg)](https://omarchy.org)
[![CPU: Ryzen 7 7800X3D](https://img.shields.io/badge/CPU-Ryzen%207%207800X3D%20(96MB%20L3)-orange.svg)](#hardware--engineering-principles)
[![GPU: RTX 3070 8GB](https://img.shields.io/badge/GPU-RTX%203070%208GB-76b900.svg)](#public-repositories--benchmarks)
[![Compositor: Hyprland](https://img.shields.io/badge/Wayland-Hyprland%20%2F%20Quickshell-2dd4bf.svg)](#public-repositories--benchmarks)

## TL;DR

Systems and local-AI engineering on **8 GB VRAM + AMD 3D V-Cache (96 MiB L3)** under **Omarchy Linux (Hyprland / Wayland)**. Everything here focuses on squeezing maximum throughput out of consumer hardware—pushing **35B MoE models to 76.3 tok/s**, running **1M-vector RAG inside CPU L3 in 163 µs**, and building native Wayland/PipeWire/DKMS tooling with zero cloud lock-in.

> [!IMPORTANT]
> **Local-first by default.** Consumer 8 GB GPUs hit a VRAM wall fast; pairing `llama.cpp` hot-expert caching with Ryzen 3D V-Cache core pinning (`vcache-run -c 2-7`) and non-temporal DDR5 prefetching (`GGML_MOE_NTA=1`) turns bandwidth-starved spillovers into smooth, interactive inference.

> [!TIP]
> **Strict security & hygiene baseline.** All public repositories follow `0700`/`0600` permission isolation, `shellcheck`/clippy/unit-test gates, and pre-push secret/path auditing.

## Architecture // AHS Neural Hive (L0–L5)

Hierarchical multi-tier routing topology balancing sub-millisecond L3 V-Cache retrieval, 8 GB CUDA inference, and edge/cloud overflow:

<div align="center">
  <img src="assets/neural_hive_3d.webp" alt="AHS Neural Hive 3D Pyramid Topology" width="820" />
</div>

```mermaid
flowchart LR
    L0["L0 // Core & State Machine\nAGENTS.md S1/S2/S3"]
    L1["L1 // 96 MiB 3D V-Cache (11 ns)\n1M-Vector RAG (163 µs) · Speculative N-Gram"]
    L2["L2 // 8 GB RTX 3070 CUDA\nHot MoE Experts · q8_0 KV · ComfyUI"]
    L3["L3 // Dual-Channel DDR5-6000\nCold MoE Experts (6C 2-7 · NTA Prefetch)"]
    L4["L4 // Desktop & Kernel Layer\nHyprland · Quickshell · PipeWire · DKMS"]

    L0 --> L1
    L1 <-->|"Zero-VRAM Drafting"| L2
    L2 <-->|"PCIe 4.0 x16"| L3
    L4 --> L0
```

## Public Repositories & Benchmarks

| Repository | Domain | Highlights & Measured Results |
| :--- | :--- | :--- |
| [**`zen-vcache-ai`**](https://github.com/simonezpx3/zen-vcache-ai) | Local AI / C / AVX-512 | **35B MoE @ `76.3 tok/s`** (`+25.5%` gen, `+22.2%` pp128 via `GGML_MOE_NTA=1`); **1M-vector RAG in `162.8 µs`** (`6,144 QPS`, `366 GB/s`); **1.2x–10.8x** code-editing speedup with `0 MiB` extra VRAM |
| [**`omarchy-qwenimage`**](https://github.com/simonezpx3/omarchy-qwenimage) | Generative AI / Python | **QIS** — local-first generative studio (Text-to-Image, Image-to-Image, Turbo diffusion, WD14 Danbooru interrogator, Qwen3-VL vision reverse-engineering, SIMD Lanczos resizer, ComfyUI backend) ([Omarchy Marketplace](https://omarchyplugins.com/plugin.html?id=simonez.qwenimage)) |
| [**`omarchy-bt-audio-eq`**](https://github.com/simonezpx3/omarchy-bt-audio-eq) | PipeWire / QML / Bash | Bluetooth codec & quality switcher (`LDAC`, `AAC`, `SBC-XQ`, `SBC`), PipeWire sample-rate selector, live telemetry, and 2-stage 10-band EQ with AutoEq ([Omarchy Marketplace](https://omarchyplugins.com/plugin.html?id=simonez.btquality)) |
| [**`omarchy-vkeyboard`**](https://github.com/simonezpx3/omarchy-vkeyboard) | Wayland / Quickshell | Non-focus-stealing OSK (`WlrLayer.Overlay`) with `wtype` injection, multi-language XKB switcher, and CRT Monolithic Grid styling ([Omarchy Marketplace](https://omarchyplugins.com/plugin.html?id=simonez.vkeyboard)) |
| [**`btusb-mt7902-dkms`**](https://github.com/simonezpx3/btusb-mt7902-dkms) | Linux Kernel / DKMS | Standalone DKMS driver patch & power fix for MediaTek MT7902 Bluetooth (`0489:e156`) on Arch / Omarchy kernels |

## Hardware & Engineering Principles

<details>
<summary><strong>Workstation Spec, Stack & Quickstart Commands</strong></summary>

| Component | Specification |
| :--- | :--- |
| **CPU** | AMD Ryzen 7 7800X3D (8C/16T, 96 MiB 3D V-Cache, AVX-512) |
| **GPU** | NVIDIA GeForce RTX 3070 8 GB |
| **Memory** | 32 GB Dual-Channel DDR5-6000 |
| **OS & WM** | Omarchy Linux (Arch-based) · Hyprland (Wayland) · Quickshell / Qt6 |
| **Languages** | C / C++, Python, Rust, QML / Qt6, Bash |

```bash
# Run 3D V-Cache MoE inference pinned to 6 cores (2-7)
GGML_MOE_NTA=1 ./bin/vcache-run -c 2-7 -- llama-server -m model.gguf -ngl 99 -cmoe --moe-cache-mib 4096 -t 6

# Install Omarchy plugins directly
omarchy plugin add https://github.com/simonezpx3/omarchy-qwenimage.git --enable
omarchy plugin add https://github.com/simonezpx3/omarchy-bt-audio-eq.git --enable
omarchy plugin add https://github.com/simonezpx3/omarchy-vkeyboard.git --enable
```

</details>
