---
Type: "[[Artifacts]]"
date:
tags:
---
# Context
ETW stands for Event Tracing Windows, it is a system that depends on 3 actors : 
- Controller
- Providers
- Consumers
![[ETW-1769518034794.png]]
The main idea is that every component/application that wants to log an event do it by being a `provider`, which provides data to `sessions` that are administered by a `controller`.
The data is then send to the `consumer` through `.etl` trace files (basically, ETW log file) or through `Realtime Event Delivery`.

Here's an example of what it could look like
![[ETW-1769518240130.png]]
# Usage
## Utility
Theses are especially useful because : 
- They're the original logs, they contains EVERYTHING that has happened on a machine, unlike .evtx files that are a curated list of events selected by the windows event log service (more on that later)
- They are low level logs (kernel), meaning that they're the purest possible form of logs, reveling things that .evtx files can miss due to their conception
- When the .evtx files are cleared, most of the time, ETW are not deleted cause they're a separated entity
- There is no form of retention for ETW, it is a flow of data, not a logging mechanism (that's why we have the [[eventvwr]]). If it's not logged or observed in real time, there will be no trace of it (otherwise, it would flood the filesystem in minutes)
- Typical `Consumers` are : 
	- EDRs
	- Event Viewers
	- SilkETW
	- ...

## Type of providers
There are 4 types of providers : 
- XML Manifest based : most used actually, use an manifest written in XML to define the ID, level and data structure of an event.
- WPP : Mostly used for drivers, need a symbol file from the developers to read them, that's why they're usually harder to read in the event viewer
-  TraceLogging: Modern type, the event is describe in himself, no need for XML Manifest anymore
- Classic Providers : Legacy, from before Windows Vista, the only reason it's still there is for retro-compatibility.
## How .evtx are created
![[ETW-1769520056492.png]]

# Links

# Example
## A process parent spoofing example for the next 2 screens
![[ETW-1769520294190.png]]
## Example of Sysmon incorrectly displaying parent process
![[ETW-1769520193231.png]]
## ETW snitching on the original parent process
![[ETW-1769520232694.png]]

![[ETW.excalidraw]]
