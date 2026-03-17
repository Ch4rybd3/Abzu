---
Type: "[[Artifacts]]"
date: 2026-03-16
tags:
File Extension:
Description: A registry artifact used to investigate on documents to know when they were created/accessed and the service used to open them
---
# Context
Jumplists are Windows artifacts that contains files and folders that have been launched recently.
They are located in : 
```
%AppData%\Microsoft\Windows\Recent\AutomaticDestinations
%AppData%\Microsoft\Windows\Recent\CustomDestinations
```
They contains complete `FilePaths`, `Dates (Creation, Access and Modification of the link)`, and `AppId`
Theses can be used to prove a user has accessed a file with a specific application (Notepad, Word, ...).
They can also prove a file has existed, even if the original has been deleted.
# Links

# Example
