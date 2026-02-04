---
Type: "[[Tools]]"
date: 2026-01-12
tags:
  - EVTX
  - Eric_ZImmerman
Input: .evtx
Output: .csv
Description: a parser for EVTX files to CSV ready for timeline explorer
Platform:
  - Windows
---
# Overview

# Usage
```shell
# Parse a folder of EVTX to a single csv
dotnet ~/Documents/tools/net9/EvtxeCmd/EvtxECmd.dll -d ~/Documents/tools/chainsaw/EVTX-ATTACK-SAMPLES/Lateral\ Movement/ --csv ~/Documents/exports --csvf parsed.csv

# Parse a single log file to csv
dotnet ~/Documents/tools/net9/EvtxeCmd/EvtxECmd.dll -f ~/Documents/tools/chainsaw/EVTX-ATTACK-SAMPLES/Lateral\ Movement/evtxlog.evtx --csv ~/Documents/exports --csvf parsed.csv
```

# Links

# Screenshot