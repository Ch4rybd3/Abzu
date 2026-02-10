---
Type: "[[Processes]]"
date:
tags:
---
# Context
Eradication is the next step to [[Containment]], once a compromised machine is quarantined, you can work on eradicating the malicious behavior.
Most of the time, deleting a malicious `.exe` isn't enough, you need to go through every place that could host malicious indicators and erase the traces left.
It could be : 
- Persistence : like created schedule tasks, exchange rules, created users, startup folders, ...
- Vulnerability : If the attacker used a specific vulnerability or misconfiguration to get access, you should remove it before you unquarantine the machine.

> Most of the time, it's enough to consider the machine to be clean and rolling again, but in more serious cases, you could skip this step, do an [[Acquisition]] to keep evidences, data (even corrupted) and go for a [[Recovery]] 

# Possible eradication measures
- Deleting the malicious files
- Deleting malicious schedule tasks
- Deleting malicious binaries in startup folders
- Deleting malicious services
- Deleting maliciously created users
- Deleting malicious exchange rules
- Deleting malicious registry keys

