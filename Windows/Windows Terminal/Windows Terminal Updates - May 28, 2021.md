---
creation date: 2021-05-28 20:54
modification date: Friday 28th May 2021 20:54:21
tags: ["#dev", "#windows"]
author: Jimmy Briggs
---

# Windows Terminal Updates - May 28, 2021

## Default Terminal

Set [[Windows Terminal]] as the default terminal in Windows by opening the legacy terminal (i.e. cmd.exe, powershell.exe, etc.), right clicking the title-bar, select *Properties* > *Terminal*, and select **Windows Terminal Preview** in the *Default Terminal Application* dropdown:

![[defterm-prop.png]]

*Update: this setting is now available directly from Windows Terminal Settings UI:*

![[defterm-term.png]]

## "Quake" Mode

Use the hotkey *Win + \`* to access `quake mode` which allows you to quickly open a new terminal instance from anywhere in Windows. The quake window will appear on the top half of your screen and can easily be dismissed with the same keyboard shortcut. If you want to further customize how you can summon the terminal, check out the new features we have added for [global summon on our docs site](https://docs.microsoft.com/windows/terminal/customize-settings/actions#global-commands).

👉 **Note:** You cannot bind quake mode to a keyboard shortcut that is already bound in the OS. This includes PowerToys users who have Win+\` bound for the FancyZones layout editor. The PowerToys team recently [changed their default keyboard shortcut](https://github.com/microsoft/PowerToys/pull/10751) to Win+Shift+\` to help avoid this conflict.

***
Links: 
- [[Windows Terminal]]
- [[Windows]]

Sources:
- [Windows Terminal Preview 1.9 Release | Windows Command Line (microsoft.com)](https://devblogs.microsoft.com/commandline/windows-terminal-preview-1-9-release/)
- [Windows Terminal Actions | Microsoft Docs](https://docs.microsoft.com/en-us/windows/terminal/customize-settings/actions#global-commands)
- [Get Windows Terminal Preview - Microsoft Store](https://www.microsoft.com/en-us/p/windows-terminal-preview/9n8g5rfz9xk3?rtc=1#activetab=pivot:overviewtab)

