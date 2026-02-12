---
Type: "[[Tools]]"
date: 2026-02-12
tags:
  - Azure
Input: no specific
Output: .csv
Description:
Platform:
  - Azure
---
# Overview
Purview is a tool from Azure.
It allow a user to access the UAL (Unified Audit Logs) which contains everything that has happened on an Azure tenant.
This is useful to track malicious activities like data exfiltration, mailbox compromissions, added roles and groups to malicious users, ...
This can also be use to leverage conformity issues.
# Usage
## Useful activities operation names
```
AddMemberToGroup : When a member is added to an Entra group
RemoveMemberFromGroup : When a member is removed from an Entra group
UserLoggedIn : User login through the login logs in Entra
New-InboxRule : When a mailbox rule has been created
Set-InboxRule : When a mailbox rule has been created
Set-Mailbox : Modification of a mailbox, like mail transfer, ...
MailItemsAccessed : When an email is being accessed
FileSyncDownloadedFull : When files are downloaded from Sharepoint or Onedrive
FileShared : When a file or folder is shared with externals
AnonymousLinkCreated : When an anonymous link is created to share a folder/file
SearchQueryPerformed : Search for keyworkds in the search queries of the user
SensitivityLabelApplied : Application of a label
SensitivityLabelUpdated : Update of a label
SensitivityLabelRemoved : Deletion of a label
Add-MailboxPermission : Full access on a mailbox given to a user
```
## Example
```
# User added to a group in Entra
Activities - friendly names : Added member to group
keyword Search : $groupname
```

# Links

# Screenshot