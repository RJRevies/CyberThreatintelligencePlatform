# 🐦 HoneyHawk: PowerShell-Based Windows Honeypot

**HoneyHawk** is a lightweight, script-only honeypot system designed for local Windows environments using only native tools and PowerShell — no VMs, no third-party software, and no Python.

This project simulates a "decoy sensitive file" and logs access attempts using built-in Windows audit capabilities. It is designed for environments with limited resources or for learning threat detection without additional infrastructure.

---

## 🎯 Purpose

To detect unauthorized local file access using PowerShell and native Windows logging, and to simulate the real-world use of honeypots for insider threat detection and monitoring.

---

## 🧰 Tools Used

- PowerShell (native)
- `auditpol.exe` (Windows auditing)
- Windows Event Viewer (`eventvwr.msc`)
- Windows Scheduled Tasks (optional)
- No Python, VMs, or external tools required

---

## 🔐 Features

- Creates a decoy sensitive file (`passwords.txt`)
- Enables file system auditing
- Logs all read access to the fake file (Event ID 4663)
- Optional export of log entries to `.txt`
- Cleanup script to reverse all changes

---

## 🚀 How It Works

1. Sets up a file in a special folder
2. Applies audit rules to log access
3. Monitors Security Event Logs
4. Access attempts get logged in Event Viewer

---

## 🧪 Sample Detection Output





