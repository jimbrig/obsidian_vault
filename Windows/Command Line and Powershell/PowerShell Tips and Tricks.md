---
creation date: 2021-06-05 19:40
modification date: Saturday 5th June 2021 19:40:19
tags: ["#dev", "#windows"]
author: Jimmy Briggs
---

# PowerShell Tips and Tricks

## Get-ChildItem or `gci`
'The result is {0:n0}' -f $l

```powershell
gci | where Length -lt 2mb
```

![[gciex.png]]

Help Page:

![[gci.png]]

## Command History

```powershell
cat (Get-PSReadlineOption).HistorySavePath | select -Last 200
```

## Hash

```powershell
$hash=@{"hell"=0; "worl"="d"}
$hash["hell"]
$out.GetEnumerator() | sort -Property Name | Format-Table Name, @{Expression="Value"; FormatString="n0"}
```

## Formatting Strings

Utilizing the `-f` (format) flag can be extremely useful for formatting output text strings.

See [\-f Format operator - PowerShell - SS64.com](https://ss64.com/ps/syntax-f-operator.html) for more details.

```powershell

# Display a number to 3 decimal places:  
"{0:n3}" -f 123.45678  
123.457

# Right align the first number only:  
"{0,10}" -f 4,5,6
     4

# Left and right align text:
"|{0,-10}| |{1,10}|" -f "hello", "world"
|hello     ||     world|

# Display an integer with 3 digits:  
"{0:n3}" -f [int32]12  
12.000

# Separate a number with dashes (# digit place holder):  
"{0:###-##-##}" -f 1234567  
123-45-67

# Create a list of 100 names with a padded suffix no. (Name001 → Name100):  
1..100 | % { 'Name{0:**d3**}' -f $_ }

# Convert a number to Hex:  
"{1,10} {0,10} {2,10:x}" -f "First", "Second", 255
    Second     First        FF  

# Display only the Year from a date time value:  
"{0:yyyy}" -f (Get-Date)  
2021

Display the hours and minutes from a date time value:  
"{0:hh}:{0:mm}" -f (Get-Date)  
17:52

# Reverse the order of display:  
"{2} {1,-10} {0:n3}" -f [math]::pi, "world", "hello"  
hello world 3.142

# Display a number as a percentage:  
"{0:p0}" -f 0.5  
50%

# Display a whole number padded to 5 digits:  
"{0:d5}" -f 123  
00123
```

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

## Check and Reconnect WiFi

```powershell
while ($true) {
  if (Test-Connection \-Count 4 \-Quiet \-Delay 3 www.github.com) {
  Write-Output "Internet Connection is good to go."
} else {
  Write-Output "Not connected to the internet."
  netsh wlan disconnect; Start-Sleep 2;
  netsh wlan connect name\=vino\-enhanced\-5G\-2;
}
 Get-Date
 Start-Sleep 3
}
```

## `netsh` Networking Commands

- `netsh interface ipv4 show ipstats`

![[neyshipstats.png]]

- `netsh interface ipv4 show tcpconnections`

![[netshtcp.png]]

### `NetStat`

![[netstat.png]]


### Wireless Adapter Interface

`netsh wlan show interfaces`: detailed information of your wireless adapter

![[netshwlaninterfaces.png]]

### View Wireless Driver Information

In some cases, you may also need to get driver information about your computer’s wireless adapter. You can get it with the following command:

`netsh wlan show drivers`

You should see the following screen:

![[netshdrivers.png]]

You will get relevant information about the driver currently installed on your system, including vendor, version, radio type, and wireless display support, and much more.

### Wireless Adapter Capabilities

You can also use the following command to view all supported wireless adapter capabilities:

`netsh wlan show capabilities`

You should see the detail information in the following screen:

[![](https://cdn.webservertalk.com/wp-content/uploads/p3-23.png)](https://cdn.webservertalk.com/wp-content/uploads/p3-23.png)

### View Wireless Network Profiles

When you connect to any wireless network, windows creates a wireless network profile and store it on your computer.

You can view all these profiles stored in your computer with the following command:

`netsh wlan show profiles`

You should see the following screen:

![[netshprofiles.png]]

If you want to delete any wireless network profile, run the following command:

`netsh wlan delete profile name=[profile name]`

You can also remove all profiles with the following command:

`netsh wlan delete profile *`

### Export and Import Wireless Profile

You can export your wireless network profile to the XML file with the following command:

`netsh wlan export profile name="profile name" key=clear folder=c:\`

If you want to import the wireless profile from the XML file, run the following command:

`netsh wlan add profile filename="path_and_filename.xml" interface="interface_name"`

### Find/View Wireless Network Password (no Software needed)

Some times, you may need to find your wireless network password if you forgot it or would like to share your wi-fi password with another user in your network.

If you forgot your wireless network password then you can recover it from the wireless network profile saved in your computer.

You can display it with the following command:

`netsh wlan show profile name="<wifi-name>" key=clear`

You can see the Wi-fi password/key in the **Key Content** field above.

### Generate Wireless Adapter Report

If you have any wireless connectivity issue then you can troubleshoot it by generating a detailed report with many important details.

You can create a wireless report with the following command:

`netsh wlan show wlanreport`

This will generate a report and save in the `WlanReport` folder.

You can view this report in your web browser. The reports contain a graph with much useful information such as, connectivity status, errors, summery of the network adapter, session success/failures, disconnect reasons, and a lot more.

### Netsh WLAN Help

Netsh is a simple and very powerful utility that comes with many useful options. If you don’t remember all commands, you can list all available options with the following command:

`netsh wlan`

You should see the following screen:

[![](https://cdn.webservertalk.com/wp-content/uploads/p8-8.png)](https://cdn.webservertalk.com/wp-content/uploads/p8-8.png)
## 
***
Links: 
- [[Windows]]
- [[Command Line and Powershell]]
Sources:
- [Powershell snippets · dbunger/notepad Wiki (github.com)](https://github.com/dbunger/notepad/wiki/Powershell-snippets)
- [PowerShell commands - PowerShell - SS64.com](https://ss64.com/ps/)

