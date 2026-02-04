---
Type: "[[Tools]]"
date: 2026-01-05
tags:
  - EVTX
  - Triage
Input: .evtx
Output: .csv
Description: crave through EVTX files for matches to sigma rules
Platform:
  - Linux
  - Windows
---
# Overview
Chainsaw is a really fast parser that goes through EVTX files and MFT tables.
It can be used to hunt down specific events such as : 
- Specific event IDs (like "4625")
- case-insensitives strings (like "mimikatz")
- Run a set of sigma rules through a folder of EVTX files (like SIgmaHQ)
- ...
It allows an analyst to quickly grasp what happen on a endpoint (or a set of endpoints) by shining light on what should be suspicious, even if it's low signal rules (rules that you wouldn't use in your SIEM because it would be too noisy but are useful in limited scope like admin logins, failed logins, ...)

One another useful feature is it's ability to also parse MFT tables.
# Usage
```
# Classic test using the EVTX sample files and sigma rules packaged in the release zip file
./chainsaw_x86_64-unknown-linux-gnu hunt EVTX-ATTACK-SAMPLES/ -s sigma/ --mapping mappings/sigma-event-logs-all.yml

# Search all .evtx files in the folder for a specific case-insensitive string
./chainsaw search mimikatz -i evtx_attack_samples/

# Search all .evtx files in the folder for a specific eventID
./chainsaw search -t 'Event.System.EventID: =4104' evtx_attack_samples/

# Search a specific evtx log for logon events, with a matching regex pattern, output in JSON format
./chainsaw search -e "DC[0-9].insecurebank.local" evtx_attack_samples --json
```

# Screenshot
![[Chainsaw-1767623278327.png]]
