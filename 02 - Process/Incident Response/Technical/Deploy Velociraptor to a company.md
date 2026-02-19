---
Type: "[[Processes]]"
date: 2026-02-12
tags:
---
# Context
When you're part of a DFIR team in a company that is doing DFIR, you need to get a hand with tools you're familiar with on compromised workstations, servers, and information system from a client.

To do so, you can use [[Velociraptor]].
Velociraptor is a DFIR and threat hunting EDR that aims to be deployed really fast, even in a different company/external entity.
# Steps
1. Generate the binary for the platforms you need (Windows, Linux, ...) directly from the server artifacts.
2. Transfer the binary to the client using your preferred method (Zipped in a password protected archive in a mail, a webhost, ...)
3. The client will then need to deploy the binaries in it's information system, he can do it using : 
	1. GPO : most used way, easy to use, allow to deploy the binary on windows workstations as a service for the whole information system
	2. SCCM, Intunes, Ansible : IS managing tool can be used to deploy the tool.
	3. Already in place EDR : Can also be used to run scripts and exe to the endpoints.
