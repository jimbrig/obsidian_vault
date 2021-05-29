---
creation date: 2021-05-28 21:58
modification date: Friday 28th May 2021 21:58:08
tags: ["#dev", "#windows", "#computer"]
author: Jimmy Briggs
---

# Using PowerShell for Windows Security

## Check Microsoft Defender Status Using PowerShell

Before you begin using PowerShell to configure Microsoft Defender, you should first check the current status. The below command gets the detailed status of the anti-malware software installed on your Windows PC.

Once you launch Windows PowerShell as administrator, type the following command and hit Enter to verify the status of Microsoft Defender:

```powershell
Get-MpComputerStatus
```

## How to Update Microsoft Defender Using PowerShell

Antivirus software must be updated regularly to keep anti-malware definitions up-to-date. You can update Microsoft Defender through Windows PowerShell by typing the following command and pressing Enter:

```powershell
Update-MpSignature
```

After successfully executing this cmdlet command, it will download and install new Microsoft Defender definition updates if available. This command works by downloading the latest updates from the default update source, the Microsoft Update Server.

Alternatively, you can also download updates from a specific source with the following command, switching out **SourceName** for the location of your choosing.

```powershell
Update-MpSignature -UpdateSource SourceName
```

The following command will update Microsoft Defender preferences to check for definition updates every day of the week automatically:

```powershell
Set-MpPreference -SignatureScheduleDay Everyday
```

## Run a Quick Antivirus Scan Using PowerShell

Sometimes, you want to run a quick malware scan on your PC. While this is relatively easy to do through the Windows Security interface, the PowerShell command makes it even easier. To run a quick virus scan on Windows 10, type the following cmdlet command on PowerShell and press Enter:

```powershell
Start-MpScan -ScanType QuickScan
```

## Run a Full Antivirus Scan Using PowerShell

A full malware scan will check every file on your Windows PC and sometimes even externally connected USB flash drives. Navigating to a **Full Scan** on the Microsoft Defender can be troublesome, so you may consider using PowerShell to run a deep malware scan of your PC quickly. You can run a Microsoft Defender full scan using the following cmdlet command:

```powershell
Start-MpScan -ScanType FullScan
```

The full scan tends to take some time to go through every folder on your PC. You can choose to run the scan in the background using the following command:

```powershell
Start-MpScan -ScanType FullScan -AsJob
```

After successfully running the above commands, Microsoft Defender will run an in-depth full malware scan of your Windows 10 PC.

## Microsoft Defender Offline Scan

The offline scan is a powerful feature that can remove malware that is difficult to detect. The antivirus software sometimes cannot remove malware while Windows is running. Such severe malware can be safely removed from the PC using the Microsoft Defender Offline Scan.

Make sure you save all of your opened files before running the offline scan. To run an offline scan on your Windows 10 PC, enter the following command into the PowerShell console:

```powershell
Start-MpWDOScan
```

This cmdlet command will cause Windows 10 to boot in Windows Defender offline mode and scan the entire system for malware. Once your computer boots, you will see the **Windows Defender Antivirus** loading screen followed by a Command Prompt window that will display the progress of the offline scan.

Once the test is complete, you can view the offline scan report by navigating to **Windows Security>Virus & threat protection > Protection history**.

## Schedule a Quick Antivirus Scan Using PowerShell

With PowerShell, you can also schedule quick scans to take place at a routine time every day throughout the week. To schedule a quick scan on Microsoft Defender, type the following command into PowerShell and press Enter:

```powershell
Set-MpPreference -ScanScheduleQuickScanTime Scan_Time
```

You need to replace **Scan\_Time** with the 24-hour time you want to run the test. The following command schedules a quick scan for 2 PM every day:

```powershell
Set-MpPreference -ScanScheduleQuickScanTime 14:00:00
```

To reset the quick scan schedule, run the same cmdlet command without the time parameter.

## Schedule a Full Antivirus Scan Using PowerShell

You can also similarly schedule a full system scan of your Windows 10 PC with a few quick commands on PowerShell:

1.  Type the below command in PowerShell and press Enter
    
```powershell
Set-MpPreference -ScanParameters 2
```
    
2.  Enter the following command, but replace "Scan\_Day" with a number between “0” and “7”, where “0” indicates every day and numbers 1-7 indicate the specific day of the week starting from Sunday
    
```powershell
Set-MpPreference -RemediationScheduleDay Scan_Day
```
    
3.  Finally, type the below command on PowerShell and replace Scan\_Time with the 24-hour time you wish to choose
    
```powershell
Set-MpPreference -RemediationScheduleTime Scan_Time
```

You can reset the entire system scan schedule to default by choosing "8" in Step 2. After successfully configuring the full scan schedule, Microsoft Defender will automatically carry out a full system scan at the configured day and time.

## Scan Windows 10 For Malware With PowerShell

Microsoft Defender is a very powerful antivirus and has consistently been one of the top antivirus software available in the market. As a built-in free-of-cost antivirus, it is very efficient in protecting you from malware threats.

PowerShell allows you to configure Microsoft Defender through a few simple commands. These commands can update Microsoft Defender, run system scans, and even set up scheduled scans.

***
Links: [[Windows]]
Source: [How to Use PowerShell to Scan Windows 10 for Malware (makeuseof.com)](https://www.makeuseof.com/how-to-use-powershell-to-scan-windows-10-for-malware/)

