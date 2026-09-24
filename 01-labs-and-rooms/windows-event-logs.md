# Detection Engineering & Threat Intelligence

**Date:** September 25, 2026
**Platform:** TryHackMe
**Room:** Intro to Detection Engineering

## 1. Objective
Transition from passively reading logs to proactively building and managing detection rules, treating them as rigorously engineered products rather than disposable scripts.

## 2. Key Concepts Mastered
* **The Detection Lifecycle:** Utilizing frameworks like CREDO (Creation, Review, Evaluation, Deployment, and Operations) and ADS (Alerting and Detection Strategy) to structure detection pipelines.
* **Precision vs. Recall:** Balancing alert accuracy. High precision minimizes false positives (reducing alert fatigue), while high recall minimizes false negatives (preventing silent breaches).
* **The Detection Gap:** Understanding that attackers move first, and a defender's goal is to keep the gap between attacker evasion capabilities and SOC detection capabilities as narrow as possible.

## 3. Practical Application & Findings
During the lab, I analyzed the core pillars of a dedicated detection team: creation, tuning, and management. I mapped out the toolstack required for a mature pipeline, including version control (Git/GitHub) for tracking rule logic, and lab environments (Atomic Red Team) for validating alerts before production deployment. I also evaluated common systemic failures, such as how missing log sources or parsing errors silently break detection logic during the data review and design phases.

## 4. Business Risk & Impact
Without a structured engineering lifecycle, a SOC inevitably suffers from detection library decay where old, untracked rules generate massive noise or stop working entirely due to unpatched vulnerabilities or deprecated tools. If a detection has low recall (high false negatives), sophisticated threats will slip through silently without triggering a single alarm, giving threat actors unrestricted dwell time to deploy ransomware or exfiltrate data.

## 5. Remediation & Lessons Learned
Good detections are engineered, not improvised. To maintain operational integrity, SOC teams must track detection rules in a structured backlog, assign clear ownership, and continuously test them against evolving adversary Tactics, Techniques, and Procedures (TTP drift) to ensure defenses remain accurate.
