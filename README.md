<p align="center">
  <img src="assets/CleanSweep.png" width="300"/>
</p>

# 🧹 Dave's CleanSweep

**Persistence-focused remediation engine for Windows systems**

> Designed for incident response, system cleanup, and post-infection recovery.

CleanSweep is a PowerShell-based remediation toolkit designed to detect and remove common persistence mechanisms, PUPs, and malware artifacts across **21 structured cleanup phases**.

Built for **PowerShell 3.0–7.x** with adaptive, version-aware execution.

---

## 🚀 Features

- ✅ 21-phase remediation engine  
- ✅ Removes common malware persistence mechanisms  
- ✅ Targets PUPs (Potentially Unwanted Programs)  
- ✅ Works across PowerShell versions 3.0–7.x  
- ✅ Intelligent version-aware execution logic  
- ✅ Modular and extensible design  

---

## 🧠 What It Does

CleanSweep performs structured remediation of Windows systems by:

- Identifying and removing persistence points:
  - Registry run keys  
  - Scheduled tasks  
  - Startup entries  
- Detecting suspicious or orphaned artifacts  
- Cleaning residual files, temp data, and infection vectors  
- Normalizing system state after cleanup  

---

## 🔬 Remediation Pipeline

CleanSweep follows a consistent multi-phase execution model:

``
