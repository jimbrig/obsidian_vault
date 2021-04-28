# Windows Command Prompt

# Command Line - Getting started with `CMD`

> cmd documentation: Getting started with cmd

This section provides an overview of what cmd is, and why a developer might want to use it.

It should also mention any large subjects within cmd, and link out to the related topics. Since the Documentation for cmd is new, you may need to create initial versions of those related topics.

Commands in CMD[#](https://riptutorial.com/cmd#commands-in-cmd)


-------------------------------------------------------------------

The available commands will be displayed, including a brief description, in tabular format.  
In Windows 10 the following commands are listed:

| Command     | Description                                                  |
| ----------- | ------------------------------------------------------------ |
| ASSOC       | Displays or modifies file extension associations.            |
| ATTRIB      | Displays or changes file attributes.                         |
| BREAK       | Sets or clears extended CTRL+C checking.                     |
| BCDEDIT     | Sets properties in boot database to control boot loading.    |
| CACLS       | Displays or modifies access control lists (ACLs) of files.   |
| CALL        | Calls one batch program from another.                        |
| CD          | Displays the name of or changes the current directory.       |
| CHCP        | Displays or sets the active code page number.                |
| CHDIR       | Displays the name of or changes the current directory.       |
| CHKDSK      | Checks a disk and displays a status report.                  |
| CHKNTFS     | Displays or modifies the checking of disk at boot time.      |
| CLS         | Clears the screen.                                           |
| CMD         | Starts a new instance of the Windows command interpreter.    |
| COLOR       | Sets the default console foreground and background colors.   |
| COMP        | Compares the contents of two files or sets of files.         |
| COMPACT     | Displays or alters the compression of files on NTFS partitions. |
| CONVERT     | Converts FAT volumes to NTFS. You cannot convert the         |
|             | current drive.                                               |
| COPY        | Copies one or more files to another location.                |
| DATE        | Displays or sets the date.                                   |
| DEL         | Deletes one or more files.                                   |
| DIR         | Displays a list of files and subdirectories in a directory.  |
| DISKPART    | Displays or configures Disk Partition properties.            |
| DOSKEY      | Edits command lines, recalls Windows commands, and           |
|             | creates macros.                                              |
| DRIVERQUERY | Displays current device driver status and properties.        |
| ECHO        | Displays messages, or turns command echoing on or off.       |
| ENDLOCAL    | Ends localization of environment changes in a batch file.    |
| ERASE       | Deletes one or more files.                                   |
| EXIT        | Quits the CMD.EXE program (command interpreter).             |
| FC          | Compares two files or sets of files, and displays the        |
|             | differences between them.                                    |
| FIND        | Searches for a text string in a file or files.               |
| FINDSTR     | Searches for strings in files.                               |
| FOR         | Runs a specified command for each file in a set of files.    |
| FORMAT      | Formats a disk for use with Windows.                         |
| FSUTIL      | Displays or configures the file system properties.           |
| FTYPE       | Displays or modifies file types used in file extension       |
|             | associations.                                                |
| GOTO        | Directs the Windows command interpreter to a labeled line in |
|             | a batch program.                                             |
| GPRESULT    | Displays Group Policy information for machine or user.       |
| GRAFTABL    | Enables Windows to display an extended character set in      |
|             | graphics mode.                                               |
| HELP        | Provides Help information for Windows commands.              |
| ICACLS      | Display, modify, backup, or restore ACLs for files and       |
|             | directories.                                                 |
| IF          | Performs conditional processing in batch programs.           |
| LABEL       | Creates, changes, or deletes the volume label of a disk.     |
| MD          | Creates a directory.                                         |
| MKDIR       | Creates a directory.                                         |
| MKLINK      | Creates Symbolic Links and Hard Links                        |
| MODE        | Configures a system device.                                  |
| MORE        | Displays output one screen at a time.                        |
| MOVE        | Moves one or more files from one directory to another        |
|             | directory.                                                   |
| OPENFILES   | Displays files opened by remote users for a file share.      |
| PATH        | Displays or sets a search path for executable files.         |
| PAUSE       | Suspends processing of a batch file and displays a message.  |
| POPD        | Restores the previous value of the current directory saved by |
|             | PUSHD.                                                       |
| PRINT       | Prints a text file.                                          |
| PROMPT      | Changes the Windows command prompt.                          |
| PUSHD       | Saves the current directory then changes it.                 |
| RD          | Removes a directory.                                         |
| RECOVER     | Recovers readable information from a bad or defective disk.  |
| REM         | Records comments (remarks) in batch files or CONFIG.SYS.     |
| REN         | Renames a file or files.                                     |
| RENAME      | Renames a file or files.                                     |
| REPLACE     | Replaces files.                                              |
| RMDIR       | Removes a directory.                                         |
| ROBOCOPY    | Advanced utility to copy files and directory trees           |
| SET         | Displays, sets, or removes Windows environment variables.    |
| SETLOCAL    | Begins localization of environment changes in a batch file.  |
| SC          | Displays or configures services (background processes).      |
| SCHTASKS    | Schedules commands and programs to run on a computer.        |
| SHIFT       | Shifts the position of replaceable parameters in batch files. |
| SHUTDOWN    | Allows proper local or remote shutdown of machine.           |
| SORT        | Sorts input.                                                 |
| START       | Starts a separate window to run a specified program or command. |
| SUBST       | Associates a path with a drive letter.                       |
| SYSTEMINFO  | Displays machine specific properties and configuration.      |
| TASKLIST    | Displays all currently running tasks including services.     |
| TASKKILL    | Kill or stop a running process or application.               |
| TIME        | Displays or sets the system time.                            |
| TITLE       | Sets the window title for a CMD.EXE session.                 |
| TREE        | Graphically displays the directory structure of a drive or   |
|             | path.                                                        |
| TYPE        | Displays the contents of a text file.                        |
| VER         | Displays the Windows version.                                |
| VERIFY      | Tells Windows whether to verify that your files are written  |
|             | correctly to a disk.                                         |
| VOL         | Displays a disk volume label and serial number.              |
| XCOPY       | Copies files and directory trees.                            |
| WMIC        | Displays WMI information inside interactive command shell.   |

To get more insight about a specific command use the `/?` option, e.g. the `tree` command gives:

    tree /?
    
    Graphically displays the folder structure of a drive or path.
    
    TREE [drive:][path] [/F] [/A]
     
       /F   Display the names of the files in each folder.
       /A   Use ASCII instead of extended characters.


Features[#](https://riptutorial.com/cmd#features)


-----------------------------------------------------

**Microsoft Command Prompt** is a _command-line interpreter_ (CLI) for the Windows operating systems.

A CLI is program intended primarily to read operating system instructions typed on a keyboard by the user. It is therefore addressed also as a _command-line interface_, to contrast it with graphical interfaces.

As these interfaces (whether textual or graphical) shield the user from directly accessing to the operating system kernel, they are also said _shells_.

Given the name of the Command Prompt executable file, `cmd.exe` , the Command Prompt is friendly named `cmd` . Given its OS piloting role, it is also said the _console_.

Like other shells, cmd can read batch of instructions from a file. In this case the cmd shell acts as a language interpreter and the file content can be regarded as an actual program. When executing these batch programs, there is no intermediate compilation phase. They are typically read, interpreted and executed line by line. Since there is no compilation, there is no production of a separated executable file. For this reason the programs are denoted _batch scripts_ or _shell scripts_.

Note that the instructions entered interactively might have a slightly different syntax from those submitted as a script, but the general principle is that what can be entered from the command line can be also put in a file for later reuse.

Hello World[#](https://riptutorial.com/cmd#hello-world)


-----------------------------------------------------------

Command Prompt batch scripts have extension `.cmd` or `.bat` , the latter for compatibility reasons.

To create a hello-word-script, you first need a place where to type it. For simple scripts, also the Windows Notepad will do. If you are serious about shell scripting, you need more effective tools. There are anyway several free alternatives, such as [Notepad++](https://notepad-plus-plus.org/).

In your designated editor type:

    echo Hello World
    pause


Save it as `hello.cmd`

If you are using "Notepad" as an editor, you should pay much attention to the saved name, as Notepad tends to add always a `.txt` extension to your files, which means that the actual name of your file might be `hello.cmd.txt` . To avoid this, in the save dialog box:

1.  In the `File name` field enter the name in double quotes, e.g. `"hello.cmd"`
2.  In the `Save as type` field select All Files, instead of the default Text Document option.

If the file has been saved properly, its icon should be similar to (Windows Vista):

[![cmd icon](images/dFGFl.png)](http://i.stack.imgur.com/dFGFl.png)

You may also consider to disable the option "Hide extension for known file types" in File Explorer folder view options. In this case, file names are always displayed with their extensions.

To execute `hello.cmd` there are two possibilities. If you are using the Windows graphical shell, just double click on its icon.

If you want to use the Command Prompt itself, you must first identify the directory where you saved `hello.cmd` . In this regard, if you open File Explorer with [![](images/B8Zit.png)](http://i.stack.imgur.com/B8Zit.png)+E. In the windows listing files, you normally read the name of the directory path containing them. You can therefore identify the directory of `hello.cmd` . Windows directory names tend to be quite long and typing them is error prone. It is better if you select and copy the directory path in the clipboard for later pasting.

Start the Command Prompt. You read a line similar to this.

    Microsoft Windows [Version ...]
    (c) ... Microsoft Corporation. All rights reserved.
     
    C:\Users\...>


The version/year of Windows of course depends on yours. In the the final line, before `>` , you read the path of the directory which is current. You should make current the directory where your script is. For this reason enter the change directory command `cd` , using a line similar to the following:

    cd <dirpath>


Instead of `<dirpath>` , paste the name of the directory you previously copied.  
To paste the directory path, in Windows 10, you just need to type Ctrl\-C, as you would in an editor. For older systems you should be able to do this by right clicking in the `cmd` window.  
After entering the command, note that current path, before `>` , changes accordingly.

You can now run your hello script by simply entering:

    hello


Comments[#](https://riptutorial.com/cmd#undefined)


------------------------------------------------------

The script prints an output similar to:

    C:\Users\...>echo Hello World
    Hello World
    
    C:\Users\...>pause
    Press any key to continue . . .


The lines hosting the symbol `>` restate the script instructions as if you had entered interactively. This can be disabled writing:

    @echo off


as the first line of your script. This might reduce the clutter, but you have less hints on what is going on, with respect to those script commands that do not give visible outputs.

The last command, `pause` , prompts you to hit any key. When you do, you exit `hello` .  
If you run `hello` from the console, you don't really need it, because, when `hello` terminates its execution, `cmd.exe` remains open and you can to read `hello` output. When double-clicking in Explorer, you start `cmd.exe` for the time necessary to execute `hello` . When `hello` terminates, `cmd.exe` does the same and you have no possibility to read `hello` output. `pause` command prevents `hello` from exiting until you hit a key, which gives also the possibility to read the output.

Finally, despite the name of the script is `hello.cmd` , it is not necessary to type the whole name, its `hello` stem is sufficient. This mechanism works for executables too, with extension `.exe` . What if there is a script `hello.cmd` and an executable `hello.exe` in the same directory? The former has priority in the Command Prompt, so `hello.cmd` will be executed.

Navigating in cmd[#](https://riptutorial.com/cmd#navigating-in-cmd)


-----------------------------------------------------------------------

One of the most common things you'll need to do in the command prompt is navigate your file system. To do this, we'll utilize the `cd` and `dir` keywords. Start by opening up a command prompt using one of the methods mentioned [here](https://riptutorial.com/cmd/example/8433/opening-a-command-prompt). You most likely see something similar to what's below, where `UserName` is your user.

    C:\Users\UserName>


Regardless of where in your file structure you are, if your system is like most, we can start with this command:

    cd C:\


This will change your current directory to the `C:\` drive. Notice how the screen now looks like this

    C:\>


Next, run a `dir` so we can see anything in the `C:\` drive

    dir


This will show you a list of files and folders with some information about them, similar to this:

[![dir command](images/f2XTr.png)](http://i.stack.imgur.com/f2XTr.png)

There's lots of good info here, but for basic navigation, we just care about the right-most column. Notice how we have a `Users` folder. That means we can run this

    cd Users


Now if you run `dir` again, you'll see all the files and folders in your `C:\Users` directory. Now, we didn't find what we wanted here, so let's go back to the parent folder. Rather than type the path to it, we can use `..` to go up one folder like so

    cd ..


Now we are back in `C:\` . If you want to go up multiple folders at once, you can put a backslash and another set of periods like so: `cd ..\..` , but we only needed one folder.

Now we want to look in that `Program Files` folder. To avoid confusing the system, it's a good idea to put quotes around the directories, especially when there are spaces in the name. So this time, we'll use this command

    C:\>cd "Program Files"


Now you are in `C:\Program Files>` and a `dir` command now will tell you anything that's in here.

So, say we get tired of wandering around to find the folder and looked up exactly where we were needing to go. Turns out it's `C:\Windows\Logs` Rather than do a `..` to `Windows` to `Logs` , we can just put the full path like so:

    cd "C:\Windows\Logs"


And that's the basics of navigating the command prompt. You can now move through all your folders so you can run your other commands in the proper places.

Opening a Command Prompt[#](https://riptutorial.com/cmd#opening-a-command-prompt)


-------------------------------------------------------------------------------------

The command prompt comes pre-installed on all Windows NT, Windows CE, OS/2 and eComStation operating systems, and exists as `cmd.exe` , typically located in `C:\Windows\system32\cmd.exe`

On Windows 7 the fastest ways to open the command prompt are:

*   Press [![enter image description here](images/B8Zit.png)](http://i.stack.imgur.com/B8Zit.png), type "cmd" and then press Enter.
    
*   Press [![enter image description here](images/B8Zit.png)](http://i.stack.imgur.com/B8Zit.png)+R, type "cmd" then then press Enter.
    

It can also be opened by navigating to the executable and double-clicking on it.

In some cases you might need to run `cmd` with elevated permissions, in this case right click and select "Run as administrator". This can also be achieved by pressing Control\+ Shift+Enter instead of Enter.

[Source](https://riptutorial.com/cmd)



### Must Know Commands

## [Assoc]

Most files in Windows are associated with a specific program that is assigned to open the file by default. At times, remembering these associations can become confusing. You can remind yourself by entering the command **assoc** to display a full list of file name extensions and program associations.

You can also extend the command to change file associations. For example, **assoc .txt=** will change the file association for text files to whatever program you enter after the equal sign. The **Assoc** command itself will reveal both the extension names and program names, which will help you properly use this command.

In Windows 10, you can view a more user-friendly interface that also lets you change file type associations on the spot. Head to **Settings (Windows + I) > Apps > Default apps > Choose default app by file type**.

## [Cipher]

Deleting files on a mechanical hard drive doesn't really delete them at all. Instead, it marks the files as no longer accessible and the space they took up as free. The files remain recoverable until the system overwrites them with new data, which can take some time.

The cipher command, however, wipes a directory by writing random data to it. To wipe your C drive, for example, you'd use the **cipher /w:d** command, which will wipe free space on the drive. The command does not overwrite undeleted data, so you will not wipe out files you need by running this command.

You can use a host of other cipher commands, however, they are generally redundant with [BitLocker enabled versions of Windows].

## [Driverquery]

Drivers remain among the most important software installed on a PC. [Improperly configured or missing drivers] can cause all sorts of trouble, so its good to have access to a list of what's on your PC. That's exactly what the **driverquery** command does. You can extend it to **driverquery -v** to obtain more information, including the directory in which the driver is installed.

For best use, I like to pipe the verbose output (`-v`) into a CSV (`-fo "csv"`) via:

```cmd
driverquery -v -fo "csv" >> My-Drivers.csv
```

## [File Compare]

You can use this command to identify differences in text between two files. It's particularly useful for writers and programmers trying to find small changes between two versions of a file. Simply type **fc** and then the directory path and file name of the two files you want to compare.

You can also extend the command in several ways. Typing **/b** compares only binary output, **/c** disregards the case of text in the comparison, and **/l** only compares ASCII text.

So, for example, you could use the following:

```cmd
fc /l "C:\\Program Files (x86)\\example1.doc" "C:\\Program Files (x86)\\example2.doc"
```

The above command compares ASCII text in two word documents.

## [ipconfig]

This command relays the IP address that your computer is currently using. However, if you're behind a router (like most computers today), you'll instead receive the local network address of the router.

Still, ipconfig is useful because of its extensions. **ipconfig /release** followed by **ipconfig /renew** can force your Windows PC into asking for a new IP address, which is useful if your computer claims one isn't available. You can also use **ipconfig /flushdns** to refresh your DNS address. These commands are great if the [Windows network troubleshooter] chokes, which does happen on occasion.

## [Netstat]

Entering the command **netstat -an** will provide you with a list of currently open ports and related IP addresses. This command will also tell you what state the port is in; listening, established, or closed.

This is a great command for when you're trying to troubleshoot devices connected to your PC or when you fear a Trojan infected your system and you're trying to locate a malicious connection.

## [Ping]

Sometimes, you need to know whether or not packets are making it to a specific networked device. That's where ping comes in handy.

Typing **ping** followed by an IP address or web domain will send a series of test packets to the specified address. If they arrive and are returned, you know the device is capable of communicating with your PC; if it fails, you know that there's something blocking communication between the device and your computer. This can help you decide if the root of the issue is an improper configuration or a failure of network hardware.

## [PathPing]

This is a more advanced version of ping that's useful if there are multiple routers between your PC and the device you're testing. Like ping, you use this command by typing **pathping** followed by the IP address, but unlike ping, pathping also relays some information about the route the test packets take.

## [Tracert]

The **tracert** command is similar to pathping. Once again, type **tracert** followed by the IP address or domain you'd like to trace. You'll receive information about each step in the route between your PC and the target. Unlike pathping, however, tracert also tracks how much time (in milliseconds) each hop between servers or devices takes.

### [Powercfg]

Powercfg is a very powerful command for managing and tracking how your computer uses energy. You can use the command **powercfg hibernate on** and **powercfg hibernate off** to manage hibernation, and you can also use the command **powercfg /a** to view the power-saving states currently available on your PC.

Another useful command is **powercfg /devicequery s1\_supported**, which displays a list of devices on your computer that support connected standby. When enabled, you can use these devices to bring your computer out of standby, even remotely. You can enable this by selecting the device in **Device Manager**, opening its properties, going to the **Power Management** tab, and then checking the **Allow this device to wake the computer** box.

**Powercfg /lastwake** will show you what device last woke your PC from a sleep state. You can use this command to troubleshoot your PC if it seems to wake from sleep at random.

You can use the **powercfg /energy** command to build a detailed power consumption report for your PC. The report saves to the directory indicated after the command finishes. This report will let you know of any system faults that might increase power consumption, like devices blocking certain sleep modes, or poorly configured to respond to your power management settings.

Windows 8 added **powercfg /batteryreport**, which provides a detailed analysis of battery use, if applicable. Normally output to your Windows user directory, the report provides details about the time and length of charge and discharge cycles, lifetime average battery life, and estimated battery capacity.

## [Shutdown]

Windows 8 introduced the shutdown command that, you guessed it, [shuts down your computer].

This is, of course, redundant with the already easily accessed shutdown button, but what's not redundant is the **shutdown /r /o** command, which restarts your PC and launches the Advanced Start Options menu, which is where you can access Safe Mode and Windows recovery utilities. This is useful if you want to restart your computer for troubleshooting purposes.

## [Systeminfo]

This command will give you a detailed configuration overview of your computer. The list covers your operating system and hardware. For example, you can look up the original Windows installation date, the last boot time, your BIOS version, total and available memory, installed hotfixes, network card configurations, and more.

Use **systeminfo /s** followed by the host name of a computer on your local network, to remotely grab the information for that system. This may require additional syntax elements for the domain, user name, and password, like this:

```cmd
systeminfo /s [host_name] /u [domain]\[user_name] /p [user_password]
```

## [System File Checker]

System File Checker is an [automatic scan and repair tool] that focuses on Windows system files.

You will need to run the command prompt with administrator privileges and enter the command **sfc /scannow**. If SFC finds any corrupt or missing files, it will automatically replace them using cached copies kept by Windows for this purpose alone. The command can require a half-hour to run on older notebooks.

## [Tasklist]

You can use the **tasklist** command to provide a current list of all tasks running on your PC. Though somewhat redundant with Task Manager, the command may sometimes find tasks hidden from view in that utility.

There's also a wide range of modifiers. **Tasklist -svc** shows services related to each task, use **tasklist -v** to obtain more detail on each task, and **tasklist -m** will locate DLL files associated with active tasks. These commands are useful for advanced troubleshooting.

Our reader Eric noted that you can "get the name of the executable associated with the particular process ID you're interested in." The command for that operation is **tasklist | find \[process id].**

## [Taskkill]

Tasks that appear in the **tasklist** command will have an executable and process ID (a four- or five-digit number) associated with them. You can force stop a program using **taskkill -im** followed by the executable's name, or **taskkill -pid** followed by the process ID. Again, this is a bit redundant with Task Manager, but you can use it to kill otherwise unresponsive or hidden programs.

## [Chkdsk]

Windows automatically marks your drive for a diagnostic chkdsk scan when symptoms indicate that a local drive has bad sectors, lost clusters, or other logical or physical errors.

If you suspect your hard drive is failing, you can manually initiate a scan. The most basic command is **chkdsk c:**, which will immediately scan the C: drive, without a need to restart the computer. If you add parameters like /f, /r, /x, or /b, such as in **chkdsk /f /r /x /b c:**, **chkdsk** will also fix errors, recover data, dismount the drive, or clear the list of bad sectors, respectively. These actions require a reboot, as they can only run with Windows powered down.

If you see **chkdsk** run at startup, let it do its thing. If it gets stuck, however, refer to the [chkdsk troubleshooting article].

## [schtasks]

**Schtasks** is your command prompt access to the Task Scheduler, one of many underrated Windows administrative tools. While you can use the GUI to manage your scheduled tasks, the command prompt lets you copy&paste complex commands to set up multiple similar tasks without having to click through various options. Ultimately, it's much easier to use, once you've committed key parameters to memory.

For example, you could schedule your computer to reboot at 11pm every Friday:

```cmd
schtasks /create /sc weekly /d FRI /tn "auto reboot computer weekly" /st 23:00 /tr "shutdown -r -f -t 10"
```

To complement your weekly reboot, you could schedule tasks to launch specific programs on startup:

```cmd
schtasks /create /sc onstart /tn "launch Chrome on startup" /tr "C:\Program Files (x86)\Google\Chrome\Application\Chrome.exe"
```

To duplicate the above command for different programs, just copy, paste, and modify it as needed.

---

## Command and Conquer Your Windows PC

This article can only give you a taste of what's hidden within the Windows command line. When including all variables, there are literally hundreds of commands. Download [Microsoft's command line reference guide] (in Edge or Internet Explorer) for advanced support and troubleshooting.

Tired of the command prompt? Time to try the [new Windows Terminal]!

[Assoc]: https://technet.microsoft.com/en-us/library/bb490865.aspx?f=255&MSPPError=-2147217396
[Cipher]: https://technet.microsoft.com/en-us/windows-server-docs/management/windows-commands/cipher
[BitLocker enabled versions of Windows]: https://www.makeuseof.com/tag/bitlocker-drive-encryption-windows-10/
[Driverquery]: https://technet.microsoft.com/en-us/library/cc731200(v=ws.11).aspx
[Improperly configured or missing drivers]: https://www.makeuseof.com/tag/take-back-control-driver-updates-windows-10/
[File Compare]: https://technet.microsoft.com/en-us/library/cc722865.aspx#XSLTsection124121120120
[ipconfig]: https://technet.microsoft.com/en-us/library/bb490921.aspx
[Windows network troubleshooter]: https://www.makeuseof.com/tag/7-simple-steps-diagnose-network-problem/
[Netstat]: https://technet.microsoft.com/en-us/library/bb490947.aspx
[Ping]: https://technet.microsoft.com/en-us/library/cc940091.aspx
[PathPing]: https://technet.microsoft.com/en-us/library/cc958876.aspx
[Tracert]: https://technet.microsoft.com/en-us/library/bb491018.aspx
[Powercfg]: https://technet.microsoft.com/en-us/library/cc748940(v=ws.10).aspx
[Shutdown]: https://technet.microsoft.com/en-us/library/bb491003.aspx
[shuts down your computer]: https://www.makeuseof.com/tag/how-to-shutdown-or-sleep-windows-10-with-a-keyboard-shortcut/
[Systeminfo]: https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/cc771190(v%3dws.11)
[System File Checker]: https://technet.microsoft.com/en-us/library/bb491008.aspx
[automatic scan and repair tool]: https://www.makeuseof.com/tag/fix-corrupted-windows-10-installation/
[Tasklist]: https://technet.microsoft.com/en-us/library/bb491010.aspx
[Taskkill]: https://technet.microsoft.com/en-us/library/bb491009.aspx
[Chkdsk]: https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/chkdsk
[chkdsk troubleshooting article]: https://www.makeuseof.com/tag/stuck-chkdsk-use-fix-right-way/
[schtasks]: https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/schtasks
[Microsoft's command line reference guide]: http://www.microsoft.com/en-us/download/details.aspx?id=2632
[new Windows Terminal]: https://www.makeuseof.com/tag/new-windows-terminal/
