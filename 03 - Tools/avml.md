---
Type: "[[Tools]]"
date: 2026-01-06
tags:
  - Memory
  - acquisition
Input: no specific
Output: .raw (memory)
Description: Dump the memory of a linux machine
Platform:
  - Linux
---
# Overview
AVML is a tool developed by Microsoft to dump the memory of a Linux machine.
It has the following advantage : 
- Single binary, no need to compile anything and easy to run on a remote machine
- Really light, follow the `minimal imprint ideology`
- Really simple to use
- Developed by `Microsoft`, which is a serious backup
- Is becoming the standard nowadays vs Lime which is starting to become a legacy thing
# Usage
```shell
# give the execute right to the binary
chmod +x avml

# default usage
./avml ~/Documents/exports/memory.raw

# make an archive
./avml ~/Documents/exports/memory.raw --compress
```

# Screenshot
![[avml-1767707125041.png]]
![[avml-1767707149914.png]]
