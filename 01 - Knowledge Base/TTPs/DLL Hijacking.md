---
Type: "[[TTP]]"
ID: T1574.001
---
# Context
Adversaries may abuse dynamic-link library files (DLLs) in order to achieve persistence, escalate privileges, and evade defenses. DLLs are libraries that contain code and data that can be simultaneously utilized by multiple programs. While DLLs are not malicious by nature, they can be abused through mechanisms such as side-loading, hijacking search order, and phantom DLL hijacking

# How to investigate

- Legitimate binary in an unusual place
- Unsigned library loaded
- A file has been renamed as a legitimate library
