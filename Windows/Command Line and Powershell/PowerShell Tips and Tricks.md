---
creation date: 2021-06-05 19:40
modification date: Saturday 5th June 2021 19:40:19
tags: ["#dev", "#windows"]
author: Jimmy Briggs
---

# PowerShell Tips and Tricks

## `GridView`

Utilizing the `Out-GridView` is a helpful way to display lists or tables of information in a user-friendly output format:

```powershell
# sort current directory by name alphabetically and view with GridView
Get-ChildItem -Path $PWD | Sort-Object | Out-GridView

# sort the current directory by file length and view with GridView
Get-ChildItem -Path C:\Test -File | Sort-Object       -Property Length


choco list | Out-GridView
winget list | Sort-Object
```

***
Links: 
Source:

