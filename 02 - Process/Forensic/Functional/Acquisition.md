---
Type: "[[Processes]]"
date:
tags:
---
# Context
When talking about acquisition, multiple things are to consider : 
- Volatility (not the tool !)
- Minimal imprint
- Integrity
- Reproducible
You can use the RFC 3227 for this : 
[RFC 3227 - Guidelines for Evidence Collection and Archiving](https://datatracker.ietf.org/doc/html/rfc3227)
## Volatility
Not all artifacts are created equals, some can last forever (for example, user listings, groups, ...), some last minutes or seconds (like the Memory) and other die instantly.
You should proceed from the most volatile to the more stable data.
One order could be : 
1. registers, cache
2.  routing table, arp cache, process table, kernel statistics, memory
3. temporary file systems
4. disk
5. remote logging and monitoring data that is relevant to the system in question
6. physical configuration, network topology
7. archival media

You need to be extra careful to not shutdown a machine until you've acquired volatile data like memory because they get flushed really fast once the machine is powered off.
## Minimal Imprint
Minimal imprints is all about "do not ruin your acquisition".
When using default and system tools, you take the risk to erase data, change timestamp, ... which can destroy evidences.
That's the main reason why we tend to do acquisition from dedicated tools from dedicated external media.
Actions done from system tools are harder to distinct and could be mixed with malicious behavior.
You could also take space directly in the disk, erasing data that's been de-allocated or worse, data from memory.
And do not forget that default/system tools "tamper" the timestamps of all files they access most of the time, this could totally ruin your evidences.
That's why tools like [[avml]] are though for minimal imprints.
## Reproducible
The steps done to acquire the artifacts should be transparent and reproducible.
You could be asked to reproduce the behavior, especially in case of insider threats or industrial spying, where the opposition could try to invalidate the evidences if they've been used without good practice.
## Integrity
Integrity is one of the most important criteria.
When acquiring data through a forensic acquisition tool, most of the time, the results are hashed to prove integrity.
This hash should be logged with additional data in a "chain of custody", making sure that the data has not been tampered with during the various manipulation that has been done.
There should be at least 2 copy of the original artifacts : 
- One for analysis
- One that has not been tampered with in any way
- (and the original obviously)
# Steps
1. Prepare your tools on an external media (USB key, network share, ...)
2. Acquire data in the volatility order
3. Get the hashed value of the artifacts collected for integrity purpose
4. Log everything in a chain of custody
5. 

