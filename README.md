<div align="center">

# ⚡ Simonez · Systems & Linux Developer ⚡

<p align="center">
  <b>Building native high-performance desktop tooling, Wayland widgets, system drivers, and autonomous AI integrations for Omarchy Linux.</b>
</p>

<p align="center">
  <a href="https://omarchyplugins.com/plugin.html?id=simonez.vkeyboard"><img src="https://img.shields.io/badge/Marketplace-Published%20%26%20Verified-10b981?style=flat-square&logo=checkmarx&logoColor=white" alt="Published & Verified"></a>
  <img src="https://img.shields.io/badge/Platform-Omarchy%20Linux-f97316?style=flat-square&logo=archlinux&logoColor=white" alt="Omarchy Linux">
  <img src="https://img.shields.io/badge/Compositor-Hyprland%20(Wayland)-2dd4bf?style=flat-square" alt="Hyprland">
  <img src="https://img.shields.io/badge/Stack-Qt6%20%7C%20QML%20%7C%20Python%20%7C%20C-c084fc?style=flat-square&logo=qt&logoColor=white" alt="Qt6 Python">
  <img src="https://img.shields.io/badge/GPU-RTX%203070%20%7C%20CUDA-76b900?style=flat-square&logo=nvidia&logoColor=white" alt="NVIDIA RTX 3070">
</p>

---

</div>

## 🌟 Featured Projects

### ⌨️ [Virtual Keyboard & Layout Switcher (`simonez.vkeyboard`)](https://github.com/simonezpx3/omarchy-vkeyboard)
**Official Omarchy Marketplace:** [Published & Verified on Omarchy Plugins](https://omarchyplugins.com/plugin.html?id=simonez.vkeyboard)

An advanced, non-focus-stealing On-Screen Virtual Keyboard (OSK) with instant `wtype` keystroke injection, system shortcut dispatching, dynamic multi-language XKB layout switching, and **Unified CRT Monolithic Grid** styling for Omarchy Linux & Hyprland.

* **Non-Focus-Stealing Architecture:** Layer-shell overlay running on `WlrLayer.Overlay` with `WlrKeyboardFocus.None` — virtual keystrokes stream directly into active target windows without stealing cursor focus.
* **Hardware Formats & Customization:** 6 selectable physical layouts (60%, 65%, 75%, TKL, Full Size, macOS), fluid opacity controls, dynamic XKB layouts repeater, and frameless mode.
* **System Dispatcher:** Seamless integration with all 227+ Omarchy & Hyprland system shortcuts via `vkeyboard-ctl dispatch`.

```bash
# 1-Click Install via Omarchy Marketplace
omarchy plugin add https://github.com/simonezpx3/omarchy-vkeyboard.git --enable
```

---

### 🚀 [Anti/Gem — AI Telemetry & Quota Monitor (`simonez.antigem`)](https://github.com/simonezpx3/antigem)

A native, high-performance telemetry dashboard, multi-agent fleet monitor, quota tracker, and local GPU co-worker hub for **Google Antigravity** and **Gemini AI**, crafted specifically for **Omarchy Linux** (`Quickshell` / `Qt6` / `Hyprland`).

* **Multi-Account Auto Failover:** Automatic failover across 3 Google AI Pro pools (`agy`, `agy2`, `agy3`) upon individual session quota exhaustion.
* **Live Quota Gauges & Context Breakdown:** Real-time 5-Hour Session Quota, 7-Day Weekly Limit, and 1M Context Window breakdown (System rules, Tool schemas, Files, History, Free headroom).
* **Local GPU & Subagent Telemetry:** Zero-token local inference monitoring (RTX 3070 CUDA, Ternary Bonsai 2 27B, Qwen Coder) and autonomous background subagents cockpit.

```bash
# 1-Click Install via Omarchy Plugin Manager
omarchy plugin add https://github.com/simonezpx3/antigem.git --enable
```

---

### 📡 [btusb-mt7902-dkms — MediaTek MT7902 Linux Bluetooth Driver](https://github.com/simonezpx3/btusb-mt7902-dkms)

Standalone DKMS kernel module bringing complete Linux hardware support for the **MediaTek MT7902** wireless/Bluetooth combo chip on modern Arch / Omarchy kernels.

* Automated DKMS rebuilds on kernel updates (`linux`, `linux-zen`, `linux-omarchy`).
* Zero latency audio streaming and full Bluetooth 5.3 headset support.

---

## 🛠️ Core Tech Stack & Battle Station

<div align="center">

| Domain | Technologies & Tooling |
| :--- | :--- |
| **Operating System** | **Omarchy Linux** (Arch-based), Linux Kernel 6.x / 7.x, systemd |
| **Display & Compositor** | **Hyprland** (Wayland), Quickshell, Qt6 Quick / QML |
| **Languages** | **QML / Qt6**, **Python 3**, **Bash / Shell**, **C / C++**, Rust |
| **AI Ecosystem** | **Google Antigravity SDK**, **Gemini Interactions API**, Ollama, FreeToken MoE |
| **Hardware Rig** | AMD Ryzen 7 7800X3D (8C/16T) · NVIDIA GeForce RTX 3070 8GB · 32GB DDR5 |
| **Engineering DNA** | Modular UNIX philosophy, strict security hygiene (`0700`/`0600`), zero leak policy |

</div>

---

## 📊 GitHub Telemetry & Stats

<div align="center">

<img src="https://github-readme-stats.vercel.app/api?username=simonezpx3&show_icons=true&theme=radical&bg_color=060a14&title_color=38bdf8&text_color=e2e6d8&icon_color=4ade80&border_color=1e293b&hide_border=false" alt="Simonez GitHub Stats" height="165" />
<img src="https://github-readme-stats.vercel.app/api/top-langs/?username=simonezpx3&layout=compact&theme=radical&bg_color=060a14&title_color=38bdf8&text_color=e2e6d8&border_color=1e293b&hide_border=false" alt="Top Languages" height="165" />

</div>

---

<div align="center">
  <sub>Built with ⚡ on Omarchy Linux · Powered by Google Antigravity & Arci</sub>
</div>
