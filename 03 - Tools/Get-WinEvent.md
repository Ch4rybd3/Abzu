---
Type: "[[Tools]]"
date:
tags:
Input:
Output:
Description:
Platform:
---
# Overview

# Usage
```Powershell
# Search in all logs from a folder for a specific message in a specific event ID, display only the date
Get-WinEvent -Path "C:\Logs\*.evtx" | Where-Object { $_.Id -eq 5142 -and $_.message -like "*PRINT*" } | Select-Object Timecreated

```

# Links

# Screenshot