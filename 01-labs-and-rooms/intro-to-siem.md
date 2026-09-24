# Intro to SIEM & Alert Triage

**Date:** September 20, 2026
**Platform:** TryHackMe
**Room:** Intro to SIEM / Junior Security Analyst Intro

## 1. Objective
Understand the fundamentals of a Security Information and Event Management (SIEM) system, including how to transition from viewing raw logs to analyzing correlated alerts in a SOC environment.

## 2. Key Concepts Mastered
* **Raw Logs vs. Correlated Alerts:** Understanding how SIEM rules filter out noise to highlight actual security incidents.
* **Alert Triage:** The process of evaluating an alert to determine if it is a true positive (actual threat) or a false positive (benign activity).

## 3. Practical Application & Findings
During the lab, I investigated a SIEM alert triggered by suspicious activity on a host machine. By analyzing the event logs, I identified that the process `cudominer.exe` caused the alert. Further log analysis revealed that the user `chris` was responsible for executing this process on the hostname `HR_02`. The alert was triggered because the process name matched the string `miner` in the SIEM's detection rules. I successfully verified this event as a True Positive.

## 4. Business Risk & Impact
The execution of `cudominer.exe` indicates a cryptojacking infection. If left unaddressed, unauthorized cryptocurrency miners will consume massive amounts of CPU/GPU resources, leading to severe system degradation on `HR_02` and potentially increasing infrastructure costs. Furthermore, the presence of an unauthorized miner often indicates a broader compromise, meaning the attacker could leverage this same access to exfiltrate sensitive HR data or deploy ransomware.

## 5. Remediation & Lessons Learned
To remediate this incident, the SOC must immediately isolate `HR_02` from the network to prevent lateral movement. The host should be scanned to remove the `cudominer.exe` payload and identify the initial infection vector (e.g., phishing email opened by user `chris`). As a preventative measure, the SIEM rule targeting the `miner` keyword should be maintained, and Endpoint Detection and Response (EDR) solutions should be configured to automatically block known cryptomining file hashes and network traffic to mining pools.
