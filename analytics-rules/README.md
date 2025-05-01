# Analytics Rules Documentation

This document explains the purpose and usage of the analytics rules implemented for Microsoft Sentinel in this project.

## Purpose

Analytics rules in Microsoft Sentinel allow automated detection of suspicious activities based on log data. These rules use Kusto Query Language (KQL) to identify potential threats and generate incidents for investigation.

## Included Rules

### 1. Multiple Failed Sign-ins Rule

**File:** `multiple_failed_signins_rule.kql`

**Description:**  
Detects users with 5 or more failed sign-in attempts from the same IP address within a 5-minute window.  
Useful for identifying brute force or password spraying attacks.

**Trigger Frequency:** 5 minutes  
**Severity:** Medium  
**Mapped Entity:** `UserPrincipalName`, `IPAddress`

---

### 2. Impossible Travel Rule

**File:** `impossible_travel_rule.kql`

**Description:**  
Flags sign-in events where a user appears to log in from two geographically distant locations (5,000+ km apart) within 60 minutes.  
Helps detect credential theft and token misuse.

**Trigger Frequency:** 15 minutes  
**Severity:** High  
**Mapped Entity:** `UserPrincipalName`, `Location`, `IPAddress`

---

## Next Steps

You can further enhance detection by:
- Tuning thresholds (e.g., distance, attempt count)
- Adding suppression logic to reduce false positives
- Linking playbooks for automatic response

Place these rule files into Microsoft Sentinel via the “Analytics” blade using scheduled query rules.


