# Real-Time Threat Detection with Microsoft Sentinel

This project demonstrates an end-to-end setup for real-time detection and response to brute-force attacks using **Microsoft Sentinel**, including automation via **Logic Apps** and analytics with **KQL queries**.

---

## Objectives

- ✅ Set up Microsoft Sentinel with Log Analytics Workspace
- ✅ Simulate brute-force attacks on a virtual machine
- ✅ Detect attacks with custom KQL rules
- ✅ Automate response using Logic Apps (e.g., email alerts)
- ✅ Visualize activity with Sentinel Workbooks

---

## Project Structure

```
/
├── analytics-rules/        → KQL detection queries
│   └── brute-force-detection.kql
├── documentation/          → PDF setup guide
│   └── End-to-End Setup_ Microsoft Sentinel & Automated Response.pdf
└── README.md               → Project overview
```

---

## Detection Rule Example

**File**: `analytics-rules/brute-force-detection.kql`

```kql
SecurityEvent
| where EventID == 4625
| project TimeGenerated, EventID, WorkstationName, Computer,
         Account, LogonTypeName, IpAddress
| extend AccountEntity = Account
| extend IpEntity = IpAddress
```

This rule detects failed login attempts, a common sign of brute-force attacks.

---

## Setup Guide

For a full, step-by-step setup, see:  
📄 `documentation/End-to-End Setup_ Microsoft Sentinel & Automated Response.pdf`

---

## How to Run

1. Create a Log Analytics Workspace
2. Enable Microsoft Sentinel
3. Create and attack a test VM (simulated brute-force)
4. Connect VM logs to Sentinel
5. Deploy the KQL rule
6. Set up Logic Apps (optional)
7. Monitor dashboards and alerts

---



## Final Notes

This is a practical demo built to showcase **real-time incident detection and response** using modern cloud security tools. Future updates will include:

- Logic App templates  
- IP auto-block playbook  
- Teams integration  

⭐️ Feel free to fork or contribute!



