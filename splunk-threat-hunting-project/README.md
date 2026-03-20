\# 🔍 Splunk Threat Hunting Project – Windows Event Log Analysis



\## 📌 Overview



This project demonstrates practical threat hunting and log analysis using Splunk Enterprise. The objective was to identify authentication anomalies, evaluate system activity, and assess logging visibility within a Windows environment.



\---



\## 🛠️ Tools \& Technologies



\* Splunk Enterprise

\* Windows Event Logs (Security \& System)

\* PowerShell

\* Virtualized Lab Environment



\---



\## 🔎 Threat Hunting Scenarios



\### 1. Failed Login Analysis



\* Query:



&#x20; ```

&#x20; index=\* EventCode=4625 | stats count by Account\_Name

&#x20; ```

\* Analysis:



&#x20; \* Identified failed authentication attempts tied to a single account.

&#x20; \* Low frequency suggests normal user behavior rather than brute-force activity.

\* Security Insight:



&#x20; \* Monitoring authentication patterns is critical for detecting credential attacks.



\---



\### 2. PowerShell Activity Assessment



\* Query:



&#x20; ```

&#x20; index=\* powershell

&#x20; ```

\* Analysis:



&#x20; \* No PowerShell-related logs were observed.

\* Security Insight:



&#x20; \* Indicates a visibility gap in command-line and script execution monitoring.

&#x20; \* PowerShell is commonly abused in post-exploitation scenarios.



\---



\### 3. Process Visibility Evaluation



\* Query:



&#x20; ```

&#x20; index=\* EventCode=1

&#x20; ```

\* Analysis:



&#x20; \* Only system-level events were available; no detailed process creation logs.

\* Security Insight:



&#x20; \* Lack of process telemetry limits detection of malicious execution.



\---



\## ⚠️ Key Findings



\* Authentication logs were available and useful for detecting login anomalies.

\* PowerShell and process-level logging were not enabled.

\* Significant visibility gaps exist in endpoint monitoring.



\---



\## 🧠 Analyst Takeaways



\* Effective threat detection depends on log coverage and data quality.

\* Windows Security logs provide authentication visibility but are insufficient alone.

\* Enhanced telemetry (Sysmon, PowerShell logging) is required for advanced threat hunting.



\---



\## 🔧 Recommendations



\* Enable PowerShell logging (Script Block Logging, Module Logging)

\* Deploy Sysmon for process creation and command-line visibility

\* Configure alerting for excessive failed login attempts

\* Build Splunk dashboards for continuous monitoring



\---



\## 📸 Evidence



Refer to the `screenshots/` directory for supporting analysis.



\---



\## 👤 Author



David Sama

Cybersecurity Analyst | Threat Hunting | SIEM | SOC Operations



