---
Type: "[[Tools]]"
date: 2026-01-19
tags:
  - Sysinternals
Input: .xml for config file
Output: no specific
Description: Installed as a service/driver, it is a boosted event logger that goes deeper than the vanilla one
Platform:
  - Windows
  - Linux
---
# Overview
Sysmon is an event logger for Windows developed and maintained by Microsoft in the Sysinternals suite.
There's also a Linux version.
It does not aim to replace the vanilla one, but to complement it.
It provide enriched event logs, but uses a different EventID table, 4688(win) = 1(sys) for example.
It also need to be manually installed and configured using an XML file
Sysmons are located in : 
- WIndows : Applications and Services Logs/Microsoft/Windows/Sysmon/Operational
- Linux : /var/log/syslog

# Usage
## Install
First thing first, you need to install the tool.

Download the tool from the official website
https://docs.microsoft.com/en-us/sysinternals/downloads/sysmon
Then install it in an admin terminal
```powershell
sysmon.exe -i -accepteula -h md5,sha256,imphash -l -n
```
Once it's done, you can load a custom sysmon configuration file using : 
```powershell
sysmon.exe -c filename.xml
```
# Event IDs

| **ID** | **Event Name**              | **Windows** | **Linux** | **Description**                                       |
| ------ | --------------------------- | ----------- | --------- | ----------------------------------------------------- |
| **1**  | **Process Creation**        | ✅           | ✅         | New process started (command line, user, hashes).     |
| **2**  | **File Creation Time**      | ✅           | ❌         | File creation time changed (detects "Timestomping").  |
| **3**  | **Network Connection**      | ✅           | ✅         | TCP/UDP connections (IPs, ports, hostnames).          |
| **4**  | **Sysmon Service State**    | ✅           | ✅         | Sysmon service status (Started/Stopped).              |
| **5**  | **Process Terminated**      | ✅           | ✅         | A process has stopped.                                |
| **6**  | **Driver Loaded**           | ✅           | ❌         | Kernel driver or module loaded into the system.       |
| **7**  | **Image Loaded**            | ✅           | ❌         | DLL or executable module loaded into a process.       |
| **8**  | **CreateRemoteThread**      | ✅           | ❌         | Code injection into another process memory.           |
| **9**  | **RawAccessRead**           | ✅           | ✅         | Direct disk reading (bypassing the file system).      |
| **10** | **ProcessAccess**           | ✅           | ❌         | A process opens another (e.g., reading LSASS memory). |
| **11** | **FileCreate**              | ✅           | ✅         | A file was created or overwritten.                    |
| **12** | **RegistryEvent (Add/Del)** | ✅           | ❌         | Registry object created or deleted.                   |
| **13** | **RegistryEvent (Set)**     | ✅           | ❌         | Registry value modification.                          |
| **14** | **RegistryEvent (Rename)**  | ✅           | ❌         | Registry key or value renamed.                        |
| **15** | **FileCreateStreamHash**    | ✅           | ❌         | Creation of Alternate Data Streams (ADS).             |
| **16** | **ServiceConfigChange**     | ✅           | ✅         | Sysmon configuration has been updated.                |
| **17** | **PipeEvent (Created)**     | ✅           | ❌         | Named Pipe created for Inter-Process Comm (IPC).      |
| **18** | **PipeEvent (Connected)**   | ✅           | ❌         | Process connected to a Named Pipe.                    |
| **19** | **WmiEvent (Filter)**       | ✅           | ❌         | WMI Event Filter activity.                            |
| **20** | **WmiEvent (Consumer)**     | ✅           | ❌         | WMI Event Consumer activity.                          |
| **21** | **WmiEvent (Binding)**      | ✅           | ❌         | WMI Filter to Consumer binding.                       |
| **22** | **DNS Query**               | ✅           | ❌         | DNS lookup performed by a process.                    |
| **23** | **FileDelete**              | ✅           | ✅         | File deleted (and optionally archived).               |
| **24** | **ClipboardChange**         | ✅           | ❌         | New data copied to the clipboard.                     |
| **25** | **ProcessTampering**        | ✅           | ❌         | Process Hollowing or Herpaderping detection.          |
| **26** | **FileDeleteDetected**      | ✅           | ✅         | File deletion occurred (log only, no archive).        |
| **27** | **FileBlockExecutable**     | ✅           | ❌         | Sysmon blocked an executable file from being written. |
| **28** | **FileBlockShredding**      | ✅           | ❌         | Blocked tools trying to wipe/shred files.             |
| **29** | **FileExecutableDetected**  | ✅           | ❌         | New executable file creation logged.                  |
# Links

# Screenshot
![[Sysmon-1769521089488.png]]
![[Sysmon.excalidraw]]