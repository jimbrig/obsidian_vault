---
creation date: 2021-06-05 22:10
modification date: Saturday 5th June 2021 22:10:27
tags: ["#dev", "#windows"]
author: Jimmy Briggs
---

# Networking Commands
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
- [[Using PowerShell for Windows Security]]
 
Sources:
- [Powershell snippets · dbunger/notepad Wiki (github.com)](https://github.com/dbunger/notepad/wiki/Powershell-snippets)
- [PowerShell commands - PowerShell - SS64.com](https://ss64.com/ps/)



