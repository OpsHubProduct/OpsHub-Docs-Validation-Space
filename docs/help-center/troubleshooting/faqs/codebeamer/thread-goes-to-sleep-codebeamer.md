## Description

Slowness is observed in integration when codebeamer is configured as one of the end systems.

## Cause

This can occur because of the API throttling configuration in codebeamer. When same codebeamer instance is used by OIM for integration and other users via API or UI simultaneously with high frequency.

## Solution

**Cases:**

**Case 1. When no API throttling is configured explicitly in the Codebeamer instance:**  
**Recommendation:** Increase the API throttling limit by adding explicit API throttling, or else API throttling enforcement can be disabled by setting `"apiThrottling" : false` in the system configuration.  
If no explicit API throttling is configured in Codebeamer, the Codebeamer enforces the API throttling limit of maximum 3 API requests per second and 120 API requests per minute.

**Case 2. When API throttling is configured explicitly in the Codebeamer instance:**  
**Recommendation:** Increase the API throttling limit where the Codebeamer instance is used highly by users other than OIM users, or else API throttling enforcement can be disabled by setting `"apiThrottling" : false` in the system configuration.
