<img width="4096" height="2284" alt="Picsart_26-06-08_12-58-12-959" src="https://github.com/user-attachments/assets/62186358-82f0-4606-a4e8-37251c765906" />


# Lunaris-AOSP-3.11-QPR2-Unofficial-Signed-for-spaced
---
### **DOWNLOAD:** [**HERE**](https://sourceforge.net/projects/lunaris-aosp-3-11-qpr2/files/Lunaris-AOSP-spaced-Community-3.11-GMS-2026060805.zip/download)
---

### 🚀 **Changelog**

#### 🛠 **Device Tree & System Fixes**
* **Display Pipeline Optimization:** Hardcoded core SurfaceFlinger rendering parameters to enforce a locked 120Hz refresh floor across all UI composition threads, eliminating dynamic scaling lag.
* **Scheduler Latency Reduction:** Corrected `uclamp` min/max constraints for SurfaceFlinger scheduler paths to prioritize critical presentation tasks, drastically reducing wake jitter and micro-stutters.
* **Display Composition Fix:** Resolved a critical rendering conflict between the MediaTek Hardware Composer (HWC) and framework window blurs. By forcing client-side GLES rendering fallback (`debug.sf.disable_hwc=1`), the system now renders complex dialog shades (e.g., Package Installer) with absolute stability, completely eliminating panel flickering while preserving full system blurs.

#### 🛡 **SEPolicy & Security Hardening**
* **VNDK Policy Compliance:** Resolved persistent SEPolicy audits for `mtk_hal_neuralnetwork` by explicitly mapping read access to target VNDK symlink paths, allowing proper hardware-accelerated NeuroPilot APU initialization.
* **Thermal Telemetry Fix:** Granted `thermal_manager` native access to process statistics via `/proc/stat`, enabling precise CPU workload tracking for optimized thermal throttling heuristics.
* **Log Buffer Optimization:** Injected strategic `dontaudit` rules for non-critical userspace framework probes, reducing kernel log spam without altering the overall security posture.

#### ⚡ **Hyperion Kernel v1.1**
* **Ring Buffer De-bloat:** Patched the core MediaTek thermal driver stack (`mtk_tc` / `mtk_lvts_tc`) to suppress repetitive watchdog API failure loops (`WD API / FAILED TO GET`), reducing driver logging overhead.
* **Kernel Stability Hardening:** Hardened process-tracking routines within the `clmutt` / `clmutt_tm_pid` procfs drivers by introducing boundary tracking locks and explicit allocation fail-safes to prevent null-pointer dereferences under heavy concurrency.

---

### 📝 **Notes & Installation**
* A clean flash is highly recommended if migrating from another ROM.
* If your facing minimal screen flickering, you can fix it by yourself by flashing this [**module**](https://t.me/DEEZProjects/23).

### 🤝 **Credits & Thanks**
* Huge thanks to `@HELLINFIX` for the foundational source collaboration and device tree support.
* Thanks to `@ViaanLarryROMS` for the assistance in adding Sony Dolby.
* Thanks to @hxfuxyy for teaching me how to implement OTA updates.
---
### 🤝🏻 **Help me continue my projects?**
* Github Sponsor: [**Sponsor**](https://github.com/sponsors/daizeuz-dred)
* Sociabuzz: [**Sponsor**](https://sociabuzz.com/daizeuzdred/tribe)
---
