---
Type: "[[Processes]]"
date:
tags:
---
# Context
Recover is as important as the rest, because you do it less often, but when you need it, it becomes vital.
There is multiple things to consider when recovering.
- First of all, do the backups exist ? This is more important than you thing because a lot of time, backups are not properly tested, fail when you need them, ...
- Integrity of the save : You need to be sure that the save you'll be recovering with is not tampered with malicious content, it would be sad to recover for nothing.
- The loss of data : When recovering, you use a save that is older than the actual time, so there will be loss of data.
- You should make sure you have made a proper [[Acquisition]] of the data and artifacts on the machine before uploading a new save, this will be useful to quickly get a machine back on tracks in prod for example, while still having the possibility to investigate on what happened.

One good thing about Windows for example and the [[NTFS]] file system is that they use [[VSS]] which are a copy of the filesystem from some hours ago, meaning that if you're under a ransomware attack, you would use those VSS to get back to a previous state (considering these backups are not tampered with malicious content) 
# Some solutions to backup files
- Veeam
- Robocopy
- [[VSS]]