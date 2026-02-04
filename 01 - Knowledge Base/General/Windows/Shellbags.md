---
Type: "[[Artifacts]]"
date: 2026-01-09
tags:
  - Windows
  - Registry
---
# Context
Shellbags are really powerful artifacts, but they're not as known as the others.
They retain information on a user navigation in the filesystem using the explorer.exe.
Officially, it retains the user "browsing habits" like the window position, the size, ...
It can be used to prove : 
- The navigation pattern of an attacker in a workstation
- The fact that a user has accessed a folder (even if they say otherwise)
- The fact that a folder existed, even if it was deleted
It is a pretty hard artifact to remove, therefore, cleaning tools usually leaves them be while other things like the event logs tends to be focused by attackers to delete their traces.
# How to read them
Shellbags are stored in user registry hives and looks like this : 
![[Shellbags-1768224289597.png]]
Dan Pullega did an excellent job at explaining, in depth how they works, how to investigate them, ... https://www.4n6k.com/2013/12/shellbags-forensics-addressing.html

# What to do with them
Shellbags are useful for : 
- Knowing which folder has been interacted with (interacted =/= navigate be careful)
- Proving that a folder has existed even if with was overwritten/deleted
- Getting the historical [[MACE]] (Modified, Accessed, Created, Entry Modified) of a folder
- The name of the user who interacted with a folder
- The mean used to interact with the folder
- Find specific folders (like malicious tool folders)

> Be careful, it works only for the navigation through the explorer.exe process (file explorer window), so it's useful if an attacker has desktop access to the machine (RDP, VNC, Direct connection, ...)

# Links
https://www.4n6k.com/2013/12/shellbags-forensics-addressing.html
https://www.magnetforensics.com/fr/blog/analyse-judiciaire-de-shellbags-cles-de-registre-windows/

# Example
