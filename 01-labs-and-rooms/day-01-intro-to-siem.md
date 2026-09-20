# Day 1: Intro to SIEM & Alert Triage

**Date:** September 20, 2026
**Platform:** TryHackMe
**Room:** Intro to SIEM / Junior Security Analyst Intro

1. Objective
Understand the fundamentals of a Security Information and Event Management (SIEM) system, including how to transition from viewing raw logs to analyzing correlated alerts in a SOC environment.

2. Key Concepts Mastered
* **Raw Logs vs. Correlated Alerts:** Understanding how SIEM rules filter out noise to highlight actual security incidents.
* **Alert Triage:** The process of evaluating an alert to determine if it is a true positive (actual threat) or a false positive (benign activity).

## 3. Practical Application & Findings
During the lab, I analyzed simulated logs to identify anomalous behavior. I investigated an alert for multiple failed login attempts followed by a successful login. By analyzing the Event IDs and source IP addresses within the SIEM dashboard, I confirmed it was a successful brute-force attack against a user account.

## 4. Business Risk & Impact
If left undetected, a successful brute-force attack allows an adversary to gain unauthorized access to the network. This can lead to lateral movement, data exfiltration, or the deployment of ransomware, severely impacting business operations and data confidentiality.

## 5. Remediation & Lessons Learned
To defend against this, the SOC should enforce account lockout policies after a set number of failed attempts, require Multi-Factor Authentication (MFA) for all users, and tune the SIEM alert to trigger faster when consecutive failed logins are detected from a single IP.
