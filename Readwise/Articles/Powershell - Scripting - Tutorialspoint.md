%%
ID: 5180684
Updated: 2020-09-28
%%
![](https://readwise-assets.s3.amazonaws.com/static/images/article3.5c705a01b476.png)

# About
Title: [[Powershell - Scripting - Tutorialspoint]]
Author: [[tutorialspoint.com]]
Category: #articles
Number of Highlights: ==15==
Last Highlighted: *2020-09-28*
Readwise URL: https://readwise.io/bookreview/5180684
Source URL: https://www.tutorialspoint.com/powershell/powershell_scripting.htm


# Highlights 
Windows PowerShell is a command-line shell and scripting language designed especially for system administration. Its analogue in Linux is called as Bash Scripting. Built on the .NET Framework, Windows PowerShell helps IT professionals to control and automate the administration of the Windows operating system and applications that run on Windows Server environment.  ^93240653

---

Windows PowerShell commands, called cmdlets, let you manage the computers from the command line. Windows PowerShell providers let you access data stores, such as the Registry and Certificate Store, as easily as you access the file system.  ^93240654

---

In addition, Windows PowerShell has a rich expression parser and a fully developed scripting language. So in simple words you can complete all the tasks that you do with GUI and much more. Windows PowerShell Scripting is a fully developed scripting language and has a rich expression parser  ^93240655

---

Features  ^93240656

---

Cmdlets − Cmdlets perform common system administration tasks, for example managing the registry, services, processes, event logs, and using Windows Management Instrumentation (WMI).  ^93240657

---

Task oriented − PowerShell scripting language is task based and provide supports for existing scripts and command-line tools.  ^93240658

---

Consistent design − As cmdlets and system data stores use common syntax and have common naming conventions, data sharing is easy. The output from one cmdlet can be pipelined to another cmdlet without any manipulation.  ^93240659

---

Simple to Use − Simplified, command-based navigation lets users navigate the registry and other data stores similar to the file system navigation.  ^93240660

---

Object based − PowerShell possesses powerful object manipulation capabilities. Objects can be sent to other tools or databases directly.  ^93240661

---

Extensible interface. − PowerShell is customizable as independent software vendors and enterprise developers can build custom tools and utilities using PowerShell to administer their software.  ^93240662

---

Variables  ^93240663

---

PowerShell variables are named objects. As PowerShell works with objects, these variables are used to work with objects.  ^93240664

---

Creating variable
Variable name should start with $ and can contain alphanumeric characters and underscore in their names. A variable can be created by typing a valid variable name.

Type the following command in PowerShell ISE Console. Assuming you are in D:\test folder.

$location = Get-Location
Here we've created a variable $location and assigned it the output of Get-Location cmdlet. It now contains the current location.  ^93240665

---

Using variable
Type the following command in PowerShell ISE Console.

 $location
Output
You can see following output in PowerShell console.

Path                                                                                    
----                                                                                    
D:\test  ^93240666

---

Getting information of variable
Get-Member cmdlet can tell the type of variable being used. See the example below.

 $location | Get-Member  ^93240668

