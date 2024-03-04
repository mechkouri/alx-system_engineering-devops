# Postmortem: Web Stack Outage on March 3, 2024

## Issue Summary:
- **Duration:** March 3, 2024, 10:00 AM - 2:00 PM (UTC)
- **Impact:** The API service was down, resulting in a complete disruption of user access. Approximately 80% of users were affected, experiencing timeouts and inability to retrieve data.
- **Root Cause:** The outage was caused by an unexpected surge in API requests due to a misconfiguration in the caching layer.

## Timeline:
- **9:45 AM:** Issue detected through monitoring alerts indicating a spike in server response times.
- **9:50 AM:** Engineers investigated logs and metrics to identify the source of the performance degradation.
- **10:15 AM:** Assumed root cause to be database overload due to increased traffic.
- **10:30 AM:** Database scaling measures initiated based on initial assumptions.
- **11:00 AM:** Continued investigation revealed misconfiguration in caching layer leading to cache misses and increased load on the database.
- **11:30 AM:** Incident escalated to senior engineering team for further analysis.
- **12:00 PM:** Cache configuration corrected, and database scaling measures reverted.
- **1:00 PM:** Service gradually restored as cache warmed up and traffic stabilized.
- **2:00 PM:** Full service recovery confirmed.

## Root Cause and Resolution:
- **Root Cause:** Misconfiguration in the caching layer resulted in excessive cache misses, leading to a surge in API requests and overwhelming the backend database.
- **Resolution:** The misconfiguration was identified and corrected by adjusting cache settings to optimize cache hit rates and reduce the load on the database.

## Corrective and Preventative Measures:
- **Improvements/Fixes:**
- mplement stricter monitoring thresholds for cache performance and database load.
- Conduct regular audits of caching configurations to ensure alignment with traffic patterns.
  - Enhance documentation and training for engineers on cache management best practices.
- **Tasks to Address the Issue:**
  - Update monitoring alerts to include cache hit/miss ratios.
  - Schedule routine reviews of caching configurations by the infrastructure team.
  - Conduct a postmortem meeting to analyze the incident response process and identify areas for improvement.

