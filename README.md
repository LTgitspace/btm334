# BTM334 Audio Receiver (Archived)

## Project Status: Deprecated & Unmaintained

This repository is **no longer actively maintained or developed**. 

The hardware and firmware designs preserved here represent legacy prototype iterations based on the **Qualcomm QCC3034 (BTM334)** module and external I2S DACs (ES9023P / PCM5102A). This repository is retained strictly for historical and architectural reference.

---

## Technical Migration: ESP32 + LDAC + Custom App

Active development has fully pivoted to an **Espressif ESP32-based architecture** delivering high-resolution wireless audio paired with a dedicated control software ecosystem.

### Key Architectural Shifts

1. **Audio Codec: Sony LDAC Integration**
   * Migrated from Qualcomm proprietary codecs (aptX / aptX HD / aptX LL) to **Sony LDAC**.
   * Capable of streaming 24-bit / 96 kHz high-resolution audio at transmission bitrates up to 990 kbps across standard A2DP profiles.

2. **Core Processor: ESP32 Platform**
   * Replaced the Qualcomm QCC3034 module with an ESP32 dual-core microcontroller running open ESP-IDF firmware.
   * Native, low-jitter I2S digital audio output feeding modern high-fidelity DAC stages.
   * Dual-mode Bluetooth support (Bluetooth Classic A2DP audio sink combined with BLE for control telemetry).

3. **Custom Companion Control Application**
   * Developing a dedicated cross-platform companion application (mobile/desktop).
   * Features real-time parametric EQ control, DSP filter tuning, DAC volume control, battery telemetry, and Over-The-Air (OTA) firmware updating over BLE.

### Rationale for the Pivot
* **Toolchain & Developer Autonomy:** Qualcomm ADK 6.4.2 and MDE 2.3 operate within a closed, vendor-locked ecosystem requiring proprietary debug hardware and restrictive NDA licensing. The ESP-IDF framework provides an open-source, reproducible, and verifiable toolchain.
* **DSP & Clocking Architecture:** Qualcomm Kymera DSP stream endpoints introduced significant clock synthesis constraints (such as MCLK configuration barriers for synchronous external DACs). The ESP32 platform enables deterministic clock control and open DSP filter pipelines.
* **Audio Fidelity:** LDAC achieves significantly higher throughput (990 kbps) compared to aptX HD (576 kbps), offering true high-resolution wireless streaming.

---

## Legacy Archive Contents

The files preserved in this repository document the earlier Qualcomm iterations:
* `btm334/`: KiCad schematic, PCB layout, and mechanical symbol/footprint libraries for the BTM334 receiver revisions (v0.1 ES9023P and v0.2 PCM5102A).
* `example1/`: Qualcomm ADK 6.4.2 Kymera Sink application baseline firmware and flash configuration scripts.
* `AGENTS.md`: Original project design requirements and hardware specifications.
