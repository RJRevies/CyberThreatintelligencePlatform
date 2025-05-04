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

First, we will pull up our Terminal we will be using PowerShell. Why? because I have been learning it’s not the gear it’s the person in the seat and it is that simple, lol.  We will be using PowerShell that’s right the basics.  
![Screenshot (232)](https://github.com/user-attachments/assets/182dca79-2e0c-48db-bfa1-c24e3f76f7ea)
We need to of course set the bait which is the basis of a honey pot be advised my firewall is down and all defenses are lowered however I have IDS and IPS in play and I real-time monitoring while performing any and all projects. The following will show my steps via terminal: 
![Screenshot (232)](https://github.com/user-attachments/assets/8fd0cadd-5bd3-41cc-84c5-2d32487171df) now we need to get a look at view finder and get to event 4663 to see that it was accessed based on the following images: 
![Screenshot (237)](https://github.com/user-attachments/assets/afb80459-8923-4c12-a9f3-b25ea97185e6)

The Purpose of this project was to display the primary purpose of a Honey Pot and that it can be done on a basic hardtop and knowledge of a programming language










