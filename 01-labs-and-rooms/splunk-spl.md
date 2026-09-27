# Splunk & Search Processing Language (SPL)

**Date:** September 27, 2026
**Platform:** TryHackMe
**Room:** Splunk: Exploring SPL

## 1. Objective
Master Splunk's Search Processing Language (SPL) to efficiently query, filter, structure, and transform raw security logs into actionable threat intelligence for rapid incident response and threat hunting.

## 2. Key Concepts Mastered
* **Search Operators & Filtering:** Using explicit timeframes (`earliest`/`latest`), specific field parameters (`EventID`), and Boolean operators—understanding that Splunk evaluates `NOT`, then `OR`, and finally `AND` (lowest priority)—to ensure accurate data retrieval.
* **Structuring & Transforming Data:** Utilizing commands like `fields` to isolate relevant columns, `stats max()` to find peak numerical values, and `top` to quickly identify the most frequently occurring entities in the logs.
* **Data Enrichment & Advanced Filtering:** Applying the `iplocation` command to map raw IP addresses to geographical regions and utilizing `regex` to parse through complex string values and registry paths.

## 3. Practical Application & Findings
I utilized SPL to filter the `windowslogs` index, successfully narrowing down massive log volumes to highly specific events. By applying time modifiers, I isolated exactly 134 events within a precise one-minute window on 04/15/2022, and separately filtered for successful logon events by querying `EventID=4624` (yielding 26 specific events).

Using transforming commands, I was able to rapidly extract key indicators. I used the `top` command to identify the most active `SourceIP` on the network (`172.90.12.11`) and the most frequently executed process `Image` (`C:\windows\system32\svchost.exe`). Furthermore, I enriched the log data by piping the `SourceIp` through the `iplocation` command, tracing the event origins to California. Finally, I utilized the `regex` command to filter `TargetObject` fields for registry keys ending in "Manager," successfully identifying `HKLM\SOFTWARE\Microsoft\SecurityManager` as the most targeted path, and used `stats max(SourceProcessId)` to locate the highest process ID (`9496`).

## 4. Business Risk & Impact
Without proficient SPL skills, a SOC analyst is entirely dependent on pre-built dashboards and cannot efficiently hunt through raw data to locate specific Indicators of Compromise (IOCs). The inability to quickly filter logs by event type, correlate IP addresses to physical locations, or parse registry paths using regular expressions drastically delays incident response times. Furthermore, a lack of understanding regarding Boolean operator precedence can result in flawed queries that inadvertently hide critical security events. Rapid data transformation is essential for identifying novel threats before they result in a prolonged, un-alerted breach.

## 5. Remediation & Lessons Learned
Security operations rely heavily on the ability to turn raw data into readable intelligence. Analysts must continuously leverage commands like `top`, `stats`, and `iplocation` to build high-fidelity, customized alerts. Moving forward, a key lesson is to always use explicit grouping (parentheses) when combining Boolean operators to avoid logic errors in log retrieval. Additionally, utilizing `regex` for deep string matching and field extraction should be a standard practice when investigating suspicious registry modifications or complex malware indicators.
