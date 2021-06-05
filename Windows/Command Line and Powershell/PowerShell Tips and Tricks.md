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

Example Output:

![[Screenshot 2021-06-05 195318.png]]

## `netsh` Networking Commands

### Wireless Adapter Interface

`netsh wlan show interfaces`: detailed information of your wireless adapter

![[netshwlaninterfaces.png]]

### View Wireless Driver Information

In some cases, you may also need to get driver information about your computer’s wireless adapter. You can get it with the following command:

`netsh wlan show drivers`

You should see the following screen:

![[netshdrivers.png]]


***
Links: 
Source:

