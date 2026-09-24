# Intro to Log Analysis

**Date:** September 24, 2026
**Platform:** TryHackMe
**Room:** Intro to Log Analysis

## 1. Objective
Understand how to manually parse and analyze raw log data to identify security incidents, recognize common attack signatures, and support threat hunting operations.

## 2. Key Concepts Mastered
* **Log File Locations:** Identifying standard log paths across different systems, such as `/var/log/nginx/access.log` for Nginx web servers and `/var/log/auth.log` for Linux authentication logs[cite: 19, 22].
* **Attack Signatures:** Recognizing the specific artifacts left behind by web-based attacks, including SQL Injection (e.g., `UNION SELECT`), Cross-Site Scripting (e.g., `<script>`), and Path Traversal (e.g., `../../`)[cite: 21, 22].
* **Analysis Methodologies:** Balancing the speed of automated AI/ML analysis tools with the thorough, contextual understanding provided by manual analysis using Linux commands like `grep`[cite: 18, 23].

## 3. Practical Application & Findings
During the lab, I manually investigated web server logs to identify specific threat actor behaviors[cite: 17, 21]. I successfully detected an SQL injection attempt where an attacker used a single quote to escape a query parameter, followed by a `UNION SELECT` statement designed to extract data from the `users` database table[cite: 21]. Additionally, I identified a path traversal attack where the threat actor utilized the `../../` sequence in an HTTP request to attempt unauthorized access to the server's sensitive `/etc/passwd` file[cite: 22].

## 4. Business Risk & Impact
Effective log analysis is crucial for detecting security incidents and maintaining compliance with regulations like GDPR, HIPAA, and PCI DSS[cite: 17]. If web-based attacks such as XSS or SQL injection are not promptly identified within system logs, attackers can manipulate web pages, extract sensitive customer data, or bypass authentication mechanisms[cite: 21]. Furthermore, failure to detect abnormal user behavior, such as geographic anomalies or unusual login times, can result in compromised accounts remaining active on the network[cite: 20].

## 5. Remediation & Lessons Learned
While automated log analysis tools save time, their reliance on AI models can lead to false positives or completely miss never-before-seen events[cite: 23]. Therefore, a competent SOC analyst must be capable of performing manual log analysis using tools like `grep` to conduct thorough, context-aware investigations and reduce the risk of overfitting[cite: 18, 23].
