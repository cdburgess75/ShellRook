<!-- LOGO -->
<p align="center">
  <img src="assets/sk-logo-light.svg" width="220">
</p>

<!-- TITLE -->
<h1 align="center">SK – ShellKnight</h1>

<!-- TAGLINE -->
<p align="center">
  PowerShell remediation, cleanup, and operational tooling
</p>

<!-- BADGES -->
<p align="center">
  <img src="assets/badges/powershell.svg">
  <img src="assets/badges/version.svg">
  <img src="assets/badges/status.svg">
</p>

---

## ⚔️ What is ShellKnight?

ShellKnight (SK) is a collection of real-world PowerShell tooling built from actual system administration, remediation, and incident response work.

This is not a demo repo.  
These scripts exist because something needed to be fixed.

---

## 🔥 Core Engine

**Dave’s CleanSweep (v0.66)**

A **21-phase remediation pipeline** designed to:

- Detect IOC-based threats
- Remove persistence mechanisms
- Clean compromised or degraded systems
- Generate actionable reports

---

## 🧠 Capabilities

### 🛠️ Remediation
- Process termination (IOC + pattern matching)
- Service + scheduled task removal (CIM-native)
- Registry cleanup (Run keys, uninstall hives)
- Browser hijacker removal

---

### 🧬 Threat Detection
- Dynamic IOC ingestion (Neo23x0)
- MalwareBazaar hash lookups
- Defender fallback scanning
- RAT / stealer signature detection

---

### 🧠 Persistence Analysis
- WMI persistence auditing
- Hosts file inspection (C2 detection, safe ranges preserved)
- Browser policy abuse detection
- Event log correlation (4688 / 7045)

---

### 💾 System Recovery
- Disk cleanup (safe-mode approach)
- Temp / cache / update cleanup
- System state reporting

---

## ⚙️ Execution Model

``
