# Endpoint Visibility & Windows Event Logs

**Date:** September 26, 2026
**Platform:** TryHackMe
**Room:** Windows Event Logs

## 1. Objective
Understand how to parse and analyze native Windows Security, System, and Application event logs to identify unauthorized access, privilege escalation, and lateral movement across a corporate network.

## 2. Key Concepts Mastered
* **Event IDs:** Memorizing and tracking critical security indicators (e.g., 4624 Successful Logon, 4625 Failed Logon, 4688 A new process has been created).
* **Log Providers & Channels:** Navigating the Windows Event Viewer and filtering logs to separate high-fidelity security events from background system noise.
* **Tracking Lateral Movement:** Correlating logon types (e.g., Network vs. Interactive) to determine how an adversary is moving between hosts.

## 3. Practical Application & Findings
During the lab, I analyzed Windows `.evtx` log files using Event Viewer and XPath queries to investigate suspicious endpoint activity. I filtered for Security Event ID `4625` (Failed Logon) and identified a pattern indicative of a brute-force attack against a local administrator account. I subsequently correlated this with Event ID `4624` (Successful Logon) and analyzed the Logon Types. The presence of Logon Type `3` (Network) followed by Logon Type `10` (Remote Interactive) confirmed the attacker successfully compromised the account and established an RDP session for lateral movement.

## 4. Business Risk & Impact
If endpoint telemetry is not actively monitored, a SOC operates with a critical blind spot. Once an adversary bypasses network-level defenses (like firewalls and IDS), native Windows Event Logs are often the only remaining indicator of unauthorized access. Failing to monitor these logs allows threat actors to silently dump credentials, execute malicious payloads, and move laterally across the network until they achieve complete domain compromise.

## 5. Remediation & Lessons Learned
To ensure comprehensive endpoint visibility, organizations must configure Advanced Audit Policies via Group Policy Object (GPO) to capture critical events, specifically enabling Process Creation (Event ID `4688`) with command-line auditing enabled. Additionally, all critical Windows security logs must be centrally collected using Windows Event Forwarding (WEF) and ingested into the SIEM to automate alerts for anomalous RDP connections and brute-force thresholds.
