# Intro to Log Analysis

**Date:** September 24, 2026
**Platform:** TryHackMe
**Room:** Intro to Log Analysis

## 1. Objective
Understand how to manually parse and analyze raw log data to identify security incidents, recognize common attack signatures, and support threat hunting operations.

## 2. Key Concepts Mastered
* **Log File Locations:** Identifying standard log paths across different systems, such as `/var/log/nginx/access.log` for Nginx web servers and `/var/log/auth.log` for Linux authentication logs.
* **Attack Signatures:** Recognizing the specific artifacts left behind by web-based attacks, including SQL Injection (e.g., `UNION SELECT`), Cross-Site Scripting (e.g., `<script>`), and Path Traversal (e.g., `../../`).
* **Analysis Methodologies:** Balancing the speed of automated AI/ML analysis tools with the thorough, contextual understanding provided by manual analysis using Linux commands like `grep`.

## 3. Practical Application & Findings
During the lab, I manually investigated web server logs to identify specific threat actor behaviors. I successfully detected an SQL injection attempt where an attacker used a single quote to escape a query parameter, followed by a `UNION SELECT` statement designed to extract data from the `users` database table. Additionally, I identified a path traversal attack where the threat actor utilized the `../../` sequence in an HTTP request to attempt unauthorized access to the server's sensitive `/etc/passwd` file.

## 4. Business Risk & Impact
Effective log analysis is crucial for detecting security incidents and maintaining compliance with regulations like GDPR, HIPAA, and PCI DSS. If web-based attacks such as XSS or SQL injection are not promptly identified within system logs, attackers can manipulate web pages, extract sensitive customer data, or bypass authentication mechanisms. Furthermore, failure to detect abnormal user behavior, such as geographic anomalies or unusual login times, can result in compromised accounts remaining active on the network.

## 5. Remediation & Lessons Learned
While automated log analysis tools save time, their reliance on AI models can lead to false positives or completely miss never-before-seen events. Therefore, a competent SOC analyst must be capable of performing manual log analysis using tools like `grep` to conduct thorough, context-aware investigations and reduce the risk of overfitting.
