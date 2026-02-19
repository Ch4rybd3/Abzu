---
Type: "[[Tools]]"
date: 2026-02-02
tags:
  - acquisition
Input: no specific
Output: .csv
Description:
Platform:
  - Windows
  - Linux
---
# Overview

# Install
## Start velociraptor in standalone mode
### Execute the binary
Start both an agent and a server on the endpoint, using only the binary and the following command (through an admin terminal obviously) : 
```Powershell
Velociraptor-v*.exe gui
```
![[image.png]]
This will start a local instance, with most of the functionalities.
It is useful to try it out, or make a live forensic investigation directly on the endpoint.
### Limitations
Just remember that it also open the terminal on 127.0.0.1:8889 using your admin account, so everything that you try to download in the GUI is stored in your admin download folder, not your user
Also remember that since you don't have a "real" datastore, when running really large hunts with many artifacts, most of them will be cached, but some may need to be recalculate, this issue is only related to standalone instances as a real production will have a propre data store to get the results
## Production
In production, things get a little bit more complicated, but I'll try to make it easy : 
- You download the velocoraptor binary from the release page for both the workstation you'll be configuring on and the server OS you'll be installing velociraptor onto (Most of the time, Windows + Linux).
- You run the following command in your workstation :
```Powershell
Velociraptor-v*.exe config generate -i
```
![[image-1.png]]
- This will start a menu where you'll select the configuration you need
- It will generate a server.config.yaml, containing the certificate and other informations (you can finetune some elements regarding the GUI address or else in case you need, I recommand checking them)
- Once done, you can just put the server.config.yaml + the binary for the server OS on the server.
- Once it's done, for linux server, just run : 
```Shell

```
- This will generate a .deb package that you can run on your OS, it will install velociraptor and create it's service
- You'll be able to access the GUI and start investigating
## Bonus : Offline Collector
# Deploying clients
Most of the time, the clients that we will want to deploy are windows or linux, we'll start with windows as it's the most used one.
- You Can just go into the GUI>Server Artifacts>Server.Utils.CreateMSI, that's all, this artifact will generate a client config file that you can run with the appropriate binary on your client with the command : 
```Powershell

```
- It will setup the client and it will try to connect to the server using the data you've configured in the generate server config part, make sure the server is listening and the client have the correct DNS/IP to reach for.
> As an information, a client.config.yaml is just an extract of the server.config.yaml

# Connect to the console
The console is open on 2 ports : 
- 8000 : Frontend -> Where the clients try to connect
- 8889 : GUI -> Where the admins connect and interact with the platform
![[image-3.png]]
# Usage
Most useful playbooks
```
_SANS_Triage : This is easily the best bundle in term of what it covers without covering everything.
_KapeTriage : This is second, as it contains all the principals artifacts, but it has a slightly lower number that the SANS one. Useful for multiple workstations
```

Here's an example of a Notebook for Task Scheduler acquisition on Windows
```SQL
/*
# Windows.System.TaskScheduler/Analysis
*/
SELECT * FROM source(artifact="Windows.System.TaskScheduler/Analysis")
LIMIT 50
```
We can triage through it by editing the notebook and modify the VQL a bit to filter for Adobe related schedule task and remove dupplicates: 
```SQL
/*
# Windows.System.TaskScheduler/Analysis
*/
SELECT * FROM source(artifact="Windows.System.TaskScheduler/Analysis")
WHERE Command =~ 'Adobe'
GROUP BY Command, Arguments
LIMIT 50
```
![[image-4.png]]
# Links

# Screenshot
![[Velociraptor-1770048625316.png]]
![[Velociraptor-1770048634792.png]]
![[Velociraptor-1770048648072.png]]