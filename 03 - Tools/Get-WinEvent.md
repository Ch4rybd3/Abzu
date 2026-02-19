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
Get-WinEvent -Path "C:\Logs\*.evtx" | Where-Object { $_.Id -eq 5142 -and $_.message -like "*PRINT*" } | Select-Object Timecreated, Message
```

```Powershell
# Search for unsigned DLL being sideloaded in an sysmon evtx file
Get-WinEvent -FilterHashtable @{Path='C:\Logs\DLLHijack\*.evtx'; Id=7} |
    Where-Object { $_.Message -like "*Signed: false*" } |
    Format-List
```

```Powershell
# Filter for specific fields using their names
Get-WinEvent -FilterHashtable @{Path='C:\Logs\Dump\*.evtx'; Id=10} | 
    Where-Object { $_.Message -like "*lsass*" } | 
    ForEach-Object {
        # Convert the data in XML to get access to the objects names
        $eventXml = [xml]$_.ToXml()
        $data = $eventXml.Event.EventData.Data

        # Create a new object with the name of the columns you want to get
        [PSCustomObject]@{
            TimeCreated = $_.TimeCreated
            SourceImage = ($data | Where-Object Name -eq "SourceImage")."#text"
            TargetImage = ($data | Where-Object Name -eq "TargetImage")."#text"
        }
    } | Format-Table -AutoSize

```

```Powershell
# Another way to parse an event
Get-WinEvent -FilterHashtable @{Path='C:\Logs\StrangePPID\*.evtx'; Id=1} |
    ForEach-Object {
        $xml = [xml]$_.ToXml()
        $image = $xml.Event.EventData.Data | Where-Object { $_.Name -eq 'Image' } | Select-Object -ExpandProperty '#text'
        $parentImage  = $xml.Event.EventData.Data | Where-Object { $_.Name -eq 'ParentImage' } | Select-Object -ExpandProperty '#text'
        [PSCustomObject]@{
            TimeCreated  = $_.TimeCreated
            ParentImage  = $parentImage
            Image        = $image
        }
    } | Format-Table -AutoSize
```

# Links

# Screenshot