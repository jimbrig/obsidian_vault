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
Get-ChildItem -Path $PWD -File | Sort-Object -Property Length | Out-GridView

# list installed chocolatey,winget,pip,npm,etc. packages in GridView
choco list | Out-GridView
winget list | Out-GridView
pip list | Out-GridView
npm stars | Out-GridView
npm list | Out-GridView
```

***
Links: 
Source:

