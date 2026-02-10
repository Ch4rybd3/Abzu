---
Type: "[[Processes]]"
date:
tags:
---
# Context
Containment is the first thing you should do once you start an incident response (but be careful, some malwares can start wiping data if they feel like they're being contained to erase their traces, ...).
There's 2 main type of containment : 
- Short term
- Long term

## Short term containment
Short term containment is everything that is easy to setup, fast to start and allow us to immediately quarantine a machine.
It could be network quarantine through EDR, Firewall rules, ...

> Once again, be careful for malwares that can auto-destruct in case they're isolated from networks
## Long term containment
Rarely used, since most of the time, the short containment + [[Eradication]] is enough, but in some scenarios, you could set up a "dirty zone" like a dedicated VLAN or else with specific rules to analyse the endpoint over an extended period of time.
# A list of possible containment measure
- Network isolation through EDR
- Put the machine in another VLAN
- Unplugging the network cables
- Turn off the wifi
- Adding a firewall rule