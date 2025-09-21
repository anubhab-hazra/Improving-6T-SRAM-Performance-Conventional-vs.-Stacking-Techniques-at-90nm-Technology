# Improving-6T-SRAM-Performance-Conventional-vs.-Stacking-Techniques-at-90nm-Technology

Design, simulation, and comparative analysis of a **6T SRAM cell implemented in Cadence Virtuoso (90 nm) — comparing the conventional 6T topology against a stacked-transistor variant**.
This repository contains schematics, ADE/Spectre testbenches, DC/butterfly transfer analysis, read/write transient verification, and power analysis (including peak-to-peak measurements).

---

## 📌 Short description
This project implements and characterizes a **6T SRAM cell in Cadence Virtuoso and evaluates how stacking transistors affects stability and power**. Analyses include DC/butterfly curves (SNM), transient read/write validation for 0 and 1, and peak-to-peak (ptp) power comparison between conventional and stacked designs.

---

## 📝 Key results
- **Peak-to-peak (PTP) power**
  - **Conventional 6T:** 82.962 µW
  - **Stacked 6T:** 39.033 µW
  - **PTP reduction (stacked vs conventional):** ~52.95%
- **Butterfly (SNM) midpoints**
  - **Conventional 6T:** 699.283 mV, 702.204 mV
  - **Stacked 6T:** 719.7273 mV, 708.2101 mV
- **Functional verification:** Read 0 and 1 operations pass for both cells (BL/BLB differential observed; Q/QB transitions valid).
- **Static power:** Power peaks at ~148 µW (typical static consumption observed for the conventional 6T at 90nm in this study).

**Notes:** Stacked technique shows a substantial reduction in instantaneous PTP power at the cost of expected tradeoffs (possible increase in series resistance / delay) — measure read/write latencies to quantify that.

---

## 📐 Design overview
- **Cell topology:** Standard 6T — two cross-coupled inverters + two NMOS access transistors.
- **Stacked variant:** Implements transistor stacking in pull-up/pull-down paths to reduce leakage and instantaneous VDD current swings.
- **Signals:** WL (Word Line), BL / BLB (Bit Lines), Q / QB (storage nodes).
- **Operating modes:** Hold, Read (WL asserted), Write (WL asserted with BL/BLB forced).

---

## 🧪 Observations & interpretation

- **Power vs. performance tradeoff:** Stacking significantly reduces instantaneous PTP power (~52.95% here), consistent with lowered leakage/current peaks. Expect some increase in effective series resistance which may increase read/write delays.
- **Stability:** Butterfly midpoints indicate bistability — compare SNM across VDD range to evaluate low-voltage robustness.
