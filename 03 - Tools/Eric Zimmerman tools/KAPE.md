---
Type: "[[Tools]]"
date: 2026-01-14
tags:
  - acquisition
  - Eric_ZImmerman
Input: FIlepath to disk or artifacts
Output: Raw artifacts, parsed csv
Description: Triage and acquisition tool that can auto-parse the results, works for everything related to file systems and registry artifacts
Platform:
  - Windows
---
# Overview
KAPE is a forensic tool that aims to collect artifacts on a machine.
It is a really powerful tool as it does not copy the whole disk but only the interesting files (artifacts) making it a really fast and powerful tool.
It has an extensive list of artifacts that you can just toggle to define a "bundle" to collect.
It has a GUI version, `gkape` which is basically a wrapper for the cli version.
It can also use modules to post-process some artifacts (for example, passing evtx files through EvtxEcmd.exe)
# Usage
## Most basic usecase
```powershell
# A really simple command to collect the artifacts from the whole C: disk using the predefined bundle KapeTriage
.\kape.exe --tsource C: --tdest C:\Cases\Samples --target KapeTriage
```
--tsource : Source disk
--tdest : Folder for the output
--target : artifact bundle
--tflush : (Optional) Flush the output folder before starting
## A quick explanation of the bundles

| Bundle name     | Content                                                          | Usage                                  |
| --------------- | ---------------------------------------------------------------- | -------------------------------------- |
| BasicCollection | Registry, Event logs, $MFT, Prefetch                             | Really basic usage                     |
| KapeTriage      | `BasicCollection` + LNK files, Jumplists, Amcache, ScheduleTasks | 90% of what's useful for investigation |
| !SANS_Triage    | Close to the KapeTriage                                          | Close to the KapeTriage                |
| Everything      | Almost everything (cloud, browser, ...)                          | Really heavy and slow                  |
## Post-process the results with modules
```powershell
# Basic usecase + module parsing using the EZ tool suite for parsing to .csv
.\kape.exe --tsource C: --tdest C:\Cases\Samples --target KapeTriage --mdest C:\Cases\Samples --module !EZParser
```

## List targets and modules
```powershell
.\kape.exe --tlist . # list all targets
.\kape.exe --mlist . # list all modules

.\kape.exe --tlist . | findstr /i "Chrome" # list all related to chrome
```

> Don't forget to update your kape targets using the script "Get-KAPEUpdate.ps1"

> You can also open the GUI by using --gui
## Use modules on already extracted artifacts
```powershell
.\kape.exe --msource C:\Cases\Samples --mdest C:\Cases\Analyzed\Full --module !EZParser
.\kape.exe --msource C:\Cases\Logs --mdest C:\Cases\Analyzed\Logs --module EvtxEcmd
.\kape.exe --msource C:\Cases\Registry --mdest C:\Cases\Analyzed\Registry --module RECmd_AllRegs
```
# Links

# Screenshot