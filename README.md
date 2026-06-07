# Lunaris-AOSP-3.11-QPR2-Unofficial-for-spaced

### 🚀 **Changelog**

#### 🛠 **Device Tree & System Fixes**
* **Display Pipeline Optimization:** Hardcoded core SurfaceFlinger rendering parameters to enforce a locked 120Hz refresh floor across all UI composition threads, eliminating dynamic scaling lag.
* **Scheduler Latency Reduction:** Corrected `uclamp` min/max constraints for SurfaceFlinger scheduler paths to prioritize critical presentation tasks, drastically reducing wake jitter and micro-stutters.
* **Display Composition Fix:** Resolved a critical rendering conflict between the MediaTek Hardware Composer (HWC) and framework window blurs. By forcing client-side GLES rendering fallback (`debug.sf.disable_hwc=1`), the system now renders complex dialog shades (e.g., Package Installer) with absolute stability, completely eliminating panel flickering while preserving full system blurs.

#### 🌐 **Build Infrastructure & Distribution**
* **Production Security Baseline:** Transitioned the compilation pipeline from public AOSP test-signatures to private, secure production keys (`release-keys`), enforcing strict partition integrity and passing core platform security attestation.
* **Seamless OTA Deployment:** Fully integrated downstream infrastructure support for the native Over-The-Air (OTA) updater system, allowing automated metadata polling and seamless dynamic slot streaming.

#### 🛡 **SEPolicy & Security Hardening**
* **VNDK Policy Compliance:** Resolved persistent SEPolicy audits for `mtk_hal_neuralnetwork` by explicitly mapping read access to target VNDK symlink paths, allowing proper hardware-accelerated NeuroPilot APU initialization.
* **Thermal Telemetry Fix:** Granted `thermal_manager` native access to process statistics via `/proc/stat`, enabling precise CPU workload tracking for optimized thermal throttling heuristics.
* **Log Buffer Optimization:** Injected strategic `dontaudit` rules for non-critical userspace framework probes, reducing kernel log spam without altering the overall security posture.

#### ⚡ **Hyperion Kernel v1.1**
* **Ring Buffer De-bloat:** Patched the core MediaTek thermal driver stack (`mtk_tc` / `mtk_lvts_tc`) to suppress repetitive watchdog API failure loops (`WD API / FAILED TO GET`), reducing driver logging overhead.
* **Kernel Stability Hardening:** Hardened process-tracking routines within the `clmutt` / `clmutt_tm_pid` procfs drivers by introducing boundary tracking locks and explicit allocation fail-safes to prevent null-pointer dereferences under heavy concurrency.

---

### 📝 **Notes & Installation**
* A clean flash is highly recommended if migrating from an alternate device tree baseline.

### 🤝 **Credits & Thanks**
* Huge thanks to `@HELLINFIX` for the foundational source collaboration and device tree support.
* Thanks to `@ViaanLarryROMS` for the assistance in adding Sony Dolby.
* To all our community testers who captured logcats to isolate and resolve these bugs.
