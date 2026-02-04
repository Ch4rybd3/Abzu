---
Type: "[[Tools]]"
date: 2026-01-05
tags:
  - Memory
Input: .mem, .raw
Output:
Description: Investigate memory dumps using plugins
Platform:
  - Windows
  - Linux
---
# Overview
Volatility3 is a tool largely used to investigate memory dumps.
The version 3 is easier to use than the 2.6 because it does not need profiles anymore, making it a faster and easier tool.
# Usage
## Symbols
Symbols are `.json.xz` files that contains data structures for the kernel.
They are specific to kernels and therefore needed when investigating.
To pick the right one, you can just check the kernel version of the endpoint by using 
```shell
uname -r # On linux
```

![[volatility3-1767708405679.png]]

Or use the banners.Banners plugin on the dump if you don't have access to the endpoint
```shell
# Check the version of the dump (Linux, WIndows, Version, ...)
sudo tools/volatility3/vol.py -f export/memory.raw banners.Banners
```

![[volatility3-1767708439371.png]]

Symbol tables can be downloaded from the following URL : 
- [https://downloads.volatilityfoundation.org/volatility3/symbols/windows.zip](https://downloads.volatilityfoundation.org/volatility3/symbols/windows.zip)
- [https://downloads.volatilityfoundation.org/volatility3/symbols/mac.zip](https://downloads.volatilityfoundation.org/volatility3/symbols/mac.zip)
- [https://downloads.volatilityfoundation.org/volatility3/symbols/linux.zip](https://downloads.volatilityfoundation.org/volatility3/symbols/linux.zip)
By default, on WIndows, when the symbol cannot be found, it is queried, downloaded, generated and cached.
For Linux and Mac, theses should be downloaded by using the links above and placing them in the volatility3/symbol folder (do not change name and let them zipped) OR should be generated using the `dwarf2json` tool
This script can be used to quickly setup the symbols archives
```
cd /home/analyst/Documents/tools/volatility3/volatility3/symbols
wget https://downloads.volatilityfoundation.org/volatility3/symbols/windows.zip
wget https://downloads.volatilityfoundation.org/volatility3/symbols/mac.zip
wget https://downloads.volatilityfoundation.org/volatility3/symbols/linux.zip
```
(can be long, so make sure that the files are there before needing them)

You can check that volatility is properly configured by using the following command (for linux) : 
```
sudo tools/volatility3/vol.py -f export/memory.raw linux.check_symbols
```
## Commands
Remember one thing before starting to use the tool : 
/!\ THE MEMORY I... IS VOLATILE /!\
You can recover things from the volatile memory, but it's still volatile, so the things you'll be searching could have been flushed.
Not seeing anything does not mean that nothing happen, but that it could just have been flushed before you started the memory acquisition.
### Windows
```
```
### Linux
```shell
# List the processes
sudo tools/volatility3/vol.py -f export/memory.raw linux.pslist

# 
```
# Screenshot