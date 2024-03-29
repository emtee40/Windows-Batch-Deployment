# Introduction
Binary files of Windows Batch Deployment. [Click here to download the entire package.](https://github.com/AxtMueller/Windows-Batch-Deployment/archive/master.zip)

### How to test on local host?
1. Rename "InstallClient.bat.txt" to "InstallClient.bat", then run it as administrator.
2. Run "ServerTestVB6GUI.EXE", you will see the local host in the client list (its IP would be 127.0.0.1 and its status would be "Online").
3. Select the local host in the client list, then click the "Connect" button. When the status changes to "Connected", you can submit operations.

### How to use?
1. Open "InstallClient.bat.txt" with a text editor, replace 127.0.0.1:9999 with your server IP or domain name.
2. Rename "InstallClient.bat.txt" to "InstallClient.bat", run it as administrator on the computers that need to be controlled.
3. Run "ServerTestVB6GUI.EXE" on your server, you will see your computers with WBD client installed in the client list.
4. Select a client, then click the "Connect" button. When the status changes to "Connected", you can submit operations.
5. Advanced users will replace "ServerTestVB6GUI.EXE" with custom server programs based on needs.

# Turn off Microsoft SmartScreen and Windows Defender
Microsoft SmartScreen and Windows Defender prevent downloading files that containing suspicious digital signatures, so you have to turn off Microsoft SmartScreen and Windows Defender before downloading. If the files cannot be downloaded, or you cannot access the downloaded files, please paste the following code into a text editor, save the code as a batch file and execute it as administrator. After restarting, this page will be opened again. You have to [manually disable Tamper Protection](https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/manage-tamper-protection-individual-device) and restart the system before using this batch file on Windows 10 and later systems.
```
::Please first disable Windows Defender Tamper Protection manually!!!
::https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/manage-tamper-protection-individual-device
reg add "HKLM\SOFTWARE\Policies\Microsoft\Windows Defender" /v DisableAntiSpyware /t REG_DWORD /d 1 /f
reg add "HKLM\Software\Policies\Microsoft\Windows Defender" /v DisableAntiVirus /t REG_DWORD /d 1 /f
reg add "HKLM\SOFTWARE\Policies\Microsoft\Windows Defender\Real-Time Protection" /v DisableIOAVProtection /t REG_DWORD /d 1 /f
reg add "HKLM\SOFTWARE\Policies\Microsoft\Windows Defender\Real-Time Protection" /v DisableRealtimeMonitoring /t REG_DWORD /d 1 /f
reg add "HKLM\SOFTWARE\Policies\Microsoft\Windows Defender\Real-Time Protection" /v DisableBehaviorMonitoring /t REG_DWORD /d 1 /f
reg add "HKLM\SOFTWARE\Policies\Microsoft\Windows Defender\Real-Time Protection" /v DisableOnAccessProtection /t REG_DWORD /d 1 /f
reg add "HKLM\SOFTWARE\Policies\Microsoft\Windows Defender\Real-Time Protection" /v DisableScanOnRealtimeEnable /t REG_DWORD /d 1 /f
reg add "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer" /v SmartScreenEnabled /t REG_SZ /d "Off" /f
reg add "HKCU\SOFTWARE\Microsoft\Edge\SmartScreenEnabled" /v "" /t REG_DWORD /d 0 /f
reg add "HKCU\SOFTWARE\Microsoft\Edge\SmartScreenPuaEnabled" /v "" /t REG_DWORD /d 0 /f
reg add "HKCU\Software\Classes\Local Settings\Software\Microsoft\Windows\CurrentVersion\AppContainer\Storage\microsoft.microsoftedge_8wekyb3d8bbwe\MicrosoftEdge\PhishingFilter" /v EnabledV9 /t REG_DWORD /d 0 /f
reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\RunOnce" /v OpenURL1 /t REG_SZ /d "explorer.exe https://github.com/AxtMueller/Windows-Batch-Deployment/tree/master/binaries" /f
reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\RunOnce" /v OpenURL2 /t REG_SZ /d "%HOMEDRIVE%\program files\internet explorer\iexplore.exe \"https://github.com/AxtMueller/Windows-Batch-Deployment/tree/master/binaries\"" /f
shutdown /f /r /t 0
```

# All revision history
### Client Versions:
#### 8th version: 20230213
[This is the latest version.](../README.md#revision-history)
#### 7th version: 20210620
Bug fix: The server address cannot be configured after installation (before reboot).  
New file: I re-uploaded the client programs on November 11, 2021 because I signed the client programs with another digital certificate.
#### 6th version: 20210212
Bug fix: Accelerate file transfer speed.  
New feature: File transfer progress callback.
#### 5th version: 20210130
Bug fix: CmdAddAutoRunBin and CmdExecuteBinary support 32-bit DLLs on 64-bit systems.  
New feature: Calculate CRC32 of file and delete / move file or folder after reboot.  
New feature: Registry operations.  
#### 4th version: 20210111
Bug fix: BSOD may happen when querying directory.  
Bug fix: BSOD may happen when downloading file via HTTP link.
#### 3rd version: 20201111
Bug fix: Enhanced stability.
#### 2nd version: 20200505
Bug fix: Enhanced stability.
#### 1st version: 20200202
This is the first public version.
### Server Versions:
#### 4th version: 20230213
[This is the latest version.](../README.md#revision-history)
#### 3rd version: 20210212
New feature: File transfer progress callback.
#### 2nd version: 20210130
New feature: Functions of registry operations.
#### 1st version: 20200202
This is the first public version.
