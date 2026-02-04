---
Type: "[[Tools]]"
date: 2026-01-05
tags:
  - SQLite
Input: .sqlite
Output: no specific
Description: search through sqlite database for web browsers forensic, etc.
Platform:
  - Web Browser
---
# Overview
SQLite Browser is a tool that allow an analyst to quickly view, query and investigate `.sqlite` files.
SQLite files are used a lot in web browser to store things like : 
- cookies
- history
- downloads metadata (source, dest)
- keywords (everything that is typed in a search bar)
- ...
this is a goldmine when it comes to investigating because you can : 
- use a search history to determine the name of a person who stole a computer
- search for user browsing activities
- Search for malicious URLs
- Search for the source of a download
- Search for the original filename of a download to pivot in the MFT table
- ...
# Usage
## Test the tool
You can just start it from the search menu, of by typing `sqlitebrowser` in a terminal
You can open the Firefox `plaxes.sqlite` to test the tool : 
```
/home/analyst/snap/firefox/common/.mozilla/firefox/ppqe8bak.default/places.sqlite
```

This is a GUI tool, there are 2 main panels that we can use
## Database Structure
![[sqlitebrowser-1767623851459.png]]
This is how the database is structured, you can find useful information, and it's the tab where the sqlitebrowser opens to. 
## Browse Data
![[sqlitebrowser-1767623888476.png]]
The most useful tab as it contains the data, this is where you'll investigate, the meat of the sqlite file.
# Difference between the web browsers
Not all web browsers are built the same and the `.sqlite` available, their structures and the data are different from one browser to another.
But you'll often find the following SQLite files : 
- places (the main sqlite file, contains the history, downloads, ...)
- cookies
- permissions
- formhistory
- extensions
- favicons
- ...
You also have to be careful about the profiles, as for each user on a endpoint, a new profile is created, sometimes, you have multiple profiles on the same sessions, they can be labeled as "Default", "Profile 1", "username", ...
It is important to check them all as they all have their own SQLite files and therefore, forensic artifacts.
For example, a user using the "Default" profile could have used his local admin account to download a specific tool (like a keygen or something that would have been blocked with it's default user), therefore, the download would not appear in the default history but in the local admin one on the opposite of his day to day usage.

> Another huge difference lies in the timestamp format, while the number of seconds since the 01/01/1970 is a standard, some like to do their own things like Google Chrome which count MILLISECONDS since the 01/01/1601, needing to format them using the google chrome format and not the standard
# Screenshot
![[sqlitebrowser-1767624529751.png|places.sqlite]]
![[sqlitebrowser-1767624614286.png|favicons.sqlite]]
