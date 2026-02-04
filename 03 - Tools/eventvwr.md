---
Type: "[[Tools]]"
date:
tags:
  - EVTX
Input: .evtx, XML language
Output: .evtx, XML results
Description: default event browsing tool on windows
Platform:
  - Windows
---
# Overview
The event viewer is the official windows process to view events logs through a GUI.
It is a bit tedious to use, but with the proper tips, it can be useful to dig through the event logs directly without security tools
# Usage
You can use it to navigate between multiple event log files (`.evtx`), the 3 standards are under the folder `` : 
- Security
- System
- Application 
The rest is under the folder `` and contains a lot of .evtx files related to 3rd party and specifics event log files : 
- EDR
- Proxy
- Sysmon
- ...

You can filter the selected log file using the GUI, but you can also use the XML query filter to make precise queries that are unavailable through the GUI (be careful, wildcards does not works here) : 

Windows `EventID 4624` logon from `john.doe` user
```xml
<QueryList>
  <Query Id="0" Path="Security">
    <Select Path="Security">
      *[System[(EventID=4624)]]
      and
      *[EventData[Data[@Name='TargetUserName']='john.doe']]
    </Select>
  </Query>
</QueryList>
```

Sysmon `EventID 1` for `malicious.exe` started from `powershell`
```xml
<QueryList>
  <Query Id="0" Path="Microsoft-Windows-Sysmon/Operational">
    <Select Path="Microsoft-Windows-Sysmon/Operational">
      *[System[(EventID=1)]]
      and
      *[EventData[
        Data[@Name='Image']='malicious.exe' 
        or 
        Data[@Name='ParentImage']='powershell.exe'
      ]]
    </Select>
  </Query>
</QueryList>
```

# Links

# Screenshot