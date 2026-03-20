\# 🧾 Investigation Notes – Splunk Threat Hunting



\## 📅 Date



March 19, 2026



\---



\## 🎯 Objective



The objective of this investigation was to analyze Windows Event Logs using Splunk to identify authentication anomalies, evaluate system activity, and assess logging visibility within the environment.



\---



\## 🛠️ Environment



\* Splunk Enterprise (local instance)

\* Windows Event Logs (Security \& System)

\* Test host: ddob



\---



\## 🔍 Activities Performed



\### 1. Failed Login Analysis



\*\*Query:\*\*



```

index=\* EventCode=4625 | stats count by Account\_Name

```



\*\*Findings:\*\*



\* Failed login attempts were observed

\* Activity was associated with a single account

\* The frequency of failures was low



\*\*Assessment:\*\*



\* Behavior appears consistent with normal user error

\* No evidence of brute-force or credential stuffing activity



\---



\### 2. PowerShell Activity Investigation



\*\*Query:\*\*



```

index=\* powershell

```



\*\*Findings:\*\*



\* No results returned



\*\*Assessment:\*\*



\* PowerShell logging is not enabled

\* This represents a visibility gap in detecting command-line or script-based attacks



\---



\### 3. Process Monitoring Evaluation



\*\*Query:\*\*



```

index=\* EventCode=1

```



\*\*Findings:\*\*



\* Only system-level logs were available

\* No detailed process creation events observed



\*\*Assessment:\*\*



\* Endpoint visibility is limited

\* Lack of process tracking reduces detection capabilities for malicious execution



\---



\## ⚠️ Key Observations



\* Authentication logs are available and useful for detecting login anomalies

\* PowerShell and process-level logging are not enabled

\* Significant visibility gaps exist in endpoint monitoring



\---



\## 🧠 Conclusion



The investigation revealed that while basic authentication monitoring is functional, the environment lacks sufficient logging for advanced threat detection. Critical telemetry such as PowerShell and process creation logs is missing, limiting the effectiveness of threat hunting activities.



\---



\## 🔧 Recommendations



\* Enable PowerShell logging (Script Block Logging, Module Logging)

\* Deploy Sysmon for enhanced process and command-line visibility

\* Configure alerting for excessive failed login attempts

\* Improve log ingestion and monitoring coverage in Splunk



\---



\## 📌 Analyst Notes



This exercise demonstrates the importance of log completeness in a SIEM environment. Effective threat detection is highly dependent on the availability of detailed and relevant telemetry.



