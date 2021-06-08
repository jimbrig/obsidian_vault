---
creation date: 2021-06-08 14:46
modification date: Tuesday 8th June 2021 14:46:08
tags: ["#windows", "#dev"]
author: Jimmy Briggs
---

# WinSCP Mirror Backup

## Installation

Ensure WinSCP is installed an in your `PATH`:

```powershell
cinst winscp -y
refreshenv
$env:Path += "C:\Program Files (x86)\WinSCP"
```

## Synchronize

```powershell
WinSCP.exe /log=winscp.out /command "open scp://daniel:<pwd>@raspberrypi" "synchronize remote test_sync test_sync -delete" "exit"
```

To watch the log:

```powershell
gc -Wait ..\winscp.out
```

***

Links: [[Windows]] | [[Command Line and Powershell]]
Source:
- [synchronize command :: WinSCP](https://winscp.net/eng/docs/scriptcommand_synchronize)
- [WinSCP mirror backup · dbunger/notepad Wiki (github.com)](https://github.com/dbunger/notepad/wiki/WinSCP-mirror-backup)

