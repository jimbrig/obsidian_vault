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

## Cascadia Code Updates

Cascadia Code now has an italic variant with cursive letterforms. This italic variant comes by default inside the terminal and can also be downloaded from [GitHub](https://github.com/microsoft/cascadia-code/releases). Font versions without “Italic” in their name will have a standard italic without the cursive letters.

## Settings UI Updates

### Editable actions page

You can now edit your existing actions via the Actions page inside the settings UI. This makes it a lot easier to customize the keyboard shortcuts you like to use with Windows Terminal. We are still actively developing this page and we’d love any feedback you have! You can add your feedback as comments in [this issue](https://github.com/microsoft/terminal/issues/6900).

[![Image editable actions page](https://devblogs.microsoft.com/commandline/wp-content/uploads/sites/33/2021/05/editable-actions-page.png)](https://devblogs.microsoft.com/commandline/wp-content/uploads/sites/33/2021/05/editable-actions-page.png)

### Add new profile

Added a new page in the settings UI that lets you create a new profile. This page gives you the option to start a new profile from scratch or duplicate an existing profile.

[![Image add new profile](https://devblogs.microsoft.com/commandline/wp-content/uploads/sites/33/2021/05/add-new-profile.png)](https://devblogs.microsoft.com/commandline/wp-content/uploads/sites/33/2021/05/add-new-profile.png)

### Profile appearance preview window

As you edit your appearance settings of your profiles, you can now see what your changes will look like in the preview window inside the settings UI!

[![Image preview window](https://devblogs.microsoft.com/commandline/wp-content/uploads/sites/33/2021/05/preview-window.png)](https://devblogs.microsoft.com/commandline/wp-content/uploads/sites/33/2021/05/preview-window.png)

## Miscellaneous improvements

🛠️ You can now disable URL detection with the `"experimental.detectURLs"` global setting.

🛠️ The last selected pivot will remain selected when navigating through profile pages in the settings UI (Thanks [@kovdu](https://github.com/kovdu)!).

🛠️ When choosing a color scheme with the command palette, the terminal will update with a preview of each one before selecting.

🛠️ You can now remove trailing white-spaces when copying text (Thanks [@Don-Vito](https://github.com/Don-Vito)!).

## Bug fixes

🐛 The terminal will no longer crash when setting a tab color using the `--tabColor` command line argument.

🐛 The dropdown no longer randomly opens in the up direction (Thanks [@mpela81](https://github.com/mpela81)!).

🐛 Long tooltips no longer get cut off (Thanks [@Don-Vito](https://github.com/Don-Vito)!).

🐛 Clicking on the tab to focus the window now actually focuses the terminal window.

***
Links: 
- [[Windows Terminal]]
- [[Windows]]

Sources:
- [Windows Terminal Preview 1.9 Release | Windows Command Line (microsoft.com)](https://devblogs.microsoft.com/commandline/windows-terminal-preview-1-9-release/)
- [Windows Terminal Actions | Microsoft Docs](https://docs.microsoft.com/en-us/windows/terminal/customize-settings/actions#global-commands)
- [Get Windows Terminal Preview - Microsoft Store](https://www.microsoft.com/en-us/p/windows-terminal-preview/9n8g5rfz9xk3?rtc=1#activetab=pivot:overviewtab)

