---
Type: "[[Tools]]"
date: 2026-04-08
tags:
  - SIEM
  - DataLake
  - ELK
Input:
Output:
Description:
Platform:
---
# Overview

# Usage
```kql
event.code: ("11" or "12" or "13" or "14")

# Because "\" is used for evading, you need to double it
event.code: "13" and registry.key: "\\CurrentVersion\\Run\\"
```

# Links

# Screenshot