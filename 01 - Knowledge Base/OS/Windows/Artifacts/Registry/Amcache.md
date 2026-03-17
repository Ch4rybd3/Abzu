---
Type: "[[Artifacts]]"
date: 2026-03-16
tags:
File Extension:
Description: A windows registry artifact that is mainly used to determine the first time an executable was executed and it's SHA1
---
# Context
`Amcache` is a registry hive `Amcache.hve` which contains metadata on executables.
It's original purpose is for compatibility use, but it store useful data such as : 
- SHA1
- File paths
- Publisher
- date of install/exec
- driver informations

It is located here : 
```
C:\Windows\AppCompat\Programs\Amcache.hve
```
# Links

# Example
