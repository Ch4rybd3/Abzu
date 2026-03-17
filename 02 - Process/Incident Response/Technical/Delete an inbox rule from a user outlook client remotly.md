---
Type: "[[Processes]]"
date: 2026-02-26
tags:
  - Azure
  - Exchange
---
# Context
On an investigation or IR, you could need to audit a user inbox rules that they made from their outlook client.
One the the main way to do is to use the PowerShell module `ExchangeOnline
# Steps

## Connect to ExchangeOnline using Powershell
Nothing really complicated, you just type:
```Powershell
Connect-ExchangeOnline
```
Doing so, you will be prompted to login with your azure account.
Once done, you'll be able to use the ExchangeOnline module.

You can start by listing the rules in a user mailbox:
```Powershell
Get-InboxRule -Mailbox <UserName> | Format-Table Name, Description, Enabled -Wrap
```
![[Delete an inbox rule from a user outlook client remotly-1772114191158.png]]To delete a rule, you can just:
```Powershell
Remove-InboxRule -Mailbox <UserName> -Identity "<RuleName>"
```
![[Delete an inbox rule from a user outlook client remotly-1772114324230.png]]
