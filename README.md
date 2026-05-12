<!-- LOGO (auto switches for GitHub light/dark mode) -->
<p align="center">
  <picture>
    <!-- GitHub dark mode -->
    <source srcset="assets/sk-logo-light.png" media="(prefers-color-scheme: dark)">
    <!-- GitHub light mode -->
    <img src="assets/sk-logo-light.png" width="600">
  </picture>
</p>

<p align="center">
  <picture>
    <source srcset="assets/sk-logo.png">
  </picture>
</p>

**Here is the complete, single `README.md` file** — everything combined into one clean, ready-to-copy block:

```markdown
<div align="center">
  <h1>🛡️ ShellKnight</h1>
  <p><strong>Enterprise Endpoint Security & Remediation Tool</strong></p>

  <img src="https://img.shields.io/badge/PowerShell-3.0%2B-blue?style=flat-square" alt="PowerShell 3.0+"/>
  <img src="https://img.shields.io/badge/Version-0.70-success?style=flat-square" alt="v0.70"/>
  <img src="https://img.shields.io/badge/Platform-Windows-success?style=flat-square" alt="Windows"/>
  <img src="https://img.shields.io/badge/License-MIT-blue?style=flat-square" alt="MIT"/>

  <p><strong>Automated removal of PUPs, browser hijackers, adware, and malware persistence mechanisms across 21 intelligent phases.</strong></p>
</div>

---

## ✨ Features

- **21-phase remediation engine** with intelligent detection and cleanup
- **Dynamic Intelligence** — Automatically downloads latest IOCs from Neo23x0/signature-base (with disk cache + hardcoded fallback)
- **MalwareBazaar Integration** — SHA256 hash lookup with API key support
- Multi-layered AV/EDR detection (Windows Defender, Datto, Huntress, SentinelOne, CrowdStrike, etc.)
- Professional **HTML executive reports** + **JSON output** + **Syslog** forwarding
- Security & Performance **A–F Grading System**
- PowerShell 3.0 – 7.x compatible (automatically adapts behavior)
- Conservative, MSP-safe design with low false-positive risk

## 📋 Phase Overview (v0.70)

| Phase | Focus                              | Key Actions |
|-------|------------------------------------|-----------|
| 0     | Hardware & OS Detection            | Collects system info and sets capability flags |
| 1     | Dynamic Intelligence Download      | Pulls hash, filename, and C2 IOCs |
| 2     | Machine Information & Grading      | Health assessment + Security/Performance grades |
| 3     | Process Termination                | Kills known PUP/adware processes |
| 4–14  | Persistence Cleanup                | Files, browser extensions, registry, services, tasks, Run keys, WMI, Hosts file, Defender exclusions |
| **15** | **Trojan / Malware IOC Detection** | **High-severity threat hunting** |
| 16    | Reboot Requirement Check           | Detects pending reboots |
| **17** | **Malware Hash Lookups**           | MalwareBazaar → Neo23x0 → Defender fallback |
| 18    | Safe Disk Cleanup                  | Temp files, caches, logs (Recycle Bin skipped) |
| 19–21 | Reporting                          | Recent software, temp file age, Event Log IOCs |

### Phase 15: Trojan / Malware IOC Detection (Detailed)

This phase focuses on detecting more serious malware (RATs, stealers, trojans) rather than typical PUPs.

**What it scans:**
- Known malicious folder names: `njrat`, `nanocore`, `asyncrat`, `quasarrat`, `remcos`, `darkcomet`, `netwire`, `redline`, `vidar`, `lokibot`, `formbook`, `emotet`, `trickbot`, `qakbot`, etc.
- Executables dropped in risky locations (`%TEMP%`, `C:\Users\Public`, `%APPDATA%`, `%LOCALAPPDATA%`)
- Uses both hardcoded signatures and dynamic filename IOCs from Phase 1

**Important Behavior:**
- Does **NOT** auto-delete (to avoid false positives and potential breakage)
- Logs findings as `[IOC]` entries (these affect exit code and final report)
- Feeds suspicious `.exe` files into **Phase 17** for hash analysis
- Includes whitelist for legitimate droppers (e.g. CitrixReceiver.exe variants)

**Example Output:**
```
[IOC] Possible malware directory (review): C:\Users\Public\asyncrat
[IOC] EXE in drop location (review): C:\Temp\svchost32.exe | 245 KB | Created: 2026-05-10
```

### Phase 17: Malware Hash Lookups

Performs deep analysis on files flagged in Phase 15:

1. **MalwareBazaar** (primary) — Queries SHA256 hash with optional API key
2. **Neo23x0** local hash IOC list (fallback)
3. **Windows Defender** custom scan (final fallback)

**Example Output:**
```
[IOC] MALWAREBAZAAR HIT  -  badfile.exe | Family: RedLine | Tags: stealer
[IOC] NEO23x0 HASH HIT   -  suspicious.exe | SHA256: ...
```

---

## 🚀 Quick Start

1. Download `ShellKnight.ps1`
2. Run as **Administrator**:

```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force
.\ShellKnight.ps1
```

**Optional Configuration** (edit at the top of the script):
- Email reports (`$SK_Email_Enabled`)
- Syslog forwarding (`$SK_Syslog_Enabled`)
- MalwareBazaar API key (`$SK_MalwareBazaar_ApiKey`)

## 🛠 Capabilities & Notes

- Conservative removal logic on high-risk items (services, tasks, registry)
- Broad PUP coverage including: OneBrowser, OneWebSearch, SweetIM, CoolWebSearch, DriverBooster, SlimDrivers, SpyHunter, ByteFence, Segurazo, TotalAV, KMSPico, KMSAuto, and many more
- Hosts file cleanup with full RFC1918 / internal IP protection
- Event Log analysis (4688 process creation + 7045 service installs)
- Inactive local account reporting (90+ days)
- Safe disk cleanup (Recycle Bin **intentionally skipped** for user data safety)
- No automatic reboot — fully operator controlled
- Works on both workstations and servers
- Designed for MSPs, enterprise environments, and RMM tools

**Important:**
- Must be run with **Administrator privileges**
- Highly conservative on destructive actions to minimize risk

## 📊 Sample Output

**Clean Machine:**
```
ShellKnight: All Clear!  -  This machine is clean.

SECURITY GRADE:     A (92/100)
PERFORMANCE GRADE:  B (81/100)
```

**With Issues:**
```
ShellKnight is Sweeping!  -  7 issue(s) detected.
```

## 📁 Output Locations

- **Logs**: `C:\ProgramData\ShellKnight\Logs\ShellKnight_YYYY-MM-DD_HHmm.log`
- **JSON Report**: `C:\ProgramData\ShellKnight\JSON\`
- **HTML Email**: Professional executive summary with full log attached

## 📜 Changelog Highlights

**v0.70** (Current)
- Major path restructure to `C:\ProgramData\ShellKnight\`
- Full MalwareBazaar authentication support
- Expanded PUP targets and improved AV/EDR detection
- Stability and logging improvements

**v0.69**
- Email + Syslog + JSON reporting overhaul
- Large PUA/PUP signature expansion

**v0.47**
- Dynamic Intelligence system introduced

---

**Built for MSPs, IT Administrators, and Security Professionals who want clean, well-documented endpoints.**

⭐ If ShellKnight helps you keep machines clean, please star this repository!
```
