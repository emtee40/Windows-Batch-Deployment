# Introduction
Windows Batch Deployment (you can simply call it as "WBD") is a programmable and rootkit-like remote access tool, it supports from Windows XP to Windows 10 (32-bit and 64-bit). Compared with other remote access software, WBD does not have a server program in the traditional sense. WBD provides a server DLL, and users need to write server programs according to their needs. Therefore, WBD maximally meets the individual needs of users. WBD client is a kernel-mode driver, it hides its traces as much as possible, and the goal is to keep the user's attention as little as possible. WBD client can run user-defined programs when system starts, user-defined programs do not store on the disk in the form of files, and there are no startup entries in the registry. As WBD may be used illegally, when WBD client starts, it outputs a text file to the desktop or the root of system drive to inform its existence and how to uninstall it manually. Disclaimer: You can only use WBD on your computers or computers which you are allowed to access, I will not be responsible for any consequences and losses caused by the abuse of it. Until you fully understand how to use WBD, please test it in virtual machines only.

### Main Features
1. File, registry and power management.
2. Run program, driver and system shell (CMD).
3. Let specific programs start at boot without using system startup directories / registry keys.
4. The client protects itself against unauthorized uninstallation. The self-protection feature takes effect after rebooting (when the installation is complete, all features except the self-protection will work; and then reboot, all features will work). If debug mode is enabled, the self-protection feature will be disabled. If you are interested in this feature, please check [this page](https://github.com/AxtMueller/Windows-Batch-Deployment/issues/1).

### How to configure and install WBD?
1. Edit “InstallClient.bat”, fill in the IP address or domain name (including port) of your server. Note: If you use WBD on the wide area network (WAN), you must have a server. If you only use WBD on the local area network (LAN, such as at home), you can use your own PC as a server.
2. Run “InstallClient.bat” on the computers that you need access remotely.

### How to access the systems with WBD installed?
1. WBD comes with a demonstration server program, you can use it as an remote access tool without programming.
2. WBD provides DLL (both 32-bit and 64-bit) for advanced users, you can write server program based on your need.

### How to uninstall WBD?
1. Call the related function from WBD server DLL (read sample source code for details).
2. Enable system debug mode, then reboot, and then delete the service of WBD client.

### About digital signature and negative comment from Anti-Virus software
Because I don't have a digital certificate, I have to use the leaked digital certificate from HT SRL to sign WBD client drivers. As for negative comment, any program of this type is considered a virus by Anti-Virus software, so who cares.

### Share your server programs
If you want to share your server programs, please commit your programs and / or source code to "Issues" with brief description. I will add your programs to the "User-defined server program" directory if I think they are useful.

# Application Scenario Examples
1. You are an administrator of IT department. You need to perform repetitive tasks on hundreds of computers (such as updating firewall rules, [pushing notifications](binaries/user-defined-server-program/push-message-test)). I used to work in this post, this is my original purpose of making this software.  
2. You are a developer. Your software does not run properly on a few users' systems, but it cannot be replicated in your test environment, so you have to [grab some data](binaries/user-defined-server-program/dump-kernel-memory) or perform some debugging tests.  
3. You are a person with a lot of secrets. You need to [erase the data on the disk](binaries/user-defined-server-program/erase-disk-data) when your computer is stolen.  
4. You are a voyeur, you want to know what your spouse did on the computer [by taking screenshots](binaries/user-defined-server-program/periodic-screen-capture). 

# [Screenshots](/screenshots/README.md)
In order to optimize the page load speed in low quality network environments, I only placed one picture on this page. 
![image](https://raw.githubusercontent.com/AxtMueller/Windows-Batch-Deployment/master/screenshots/1.png)

# Contact
### E-MAIL: AxtMueller#gmx.de (Replace # with @)
1. If you find bugs, have constructive suggestions or would like to purchase a paid service, please let me know.  
2. You'd better write E-MAIL in English or German, I only reply to E-MAILs that I am interested in.
3. In order to disclose as little personal information as possible (IP address, online time, etc.), I do not use instant messaging. Just write what you want in the E-MAIL.
4. In order to reduce the impact of the Internet on real life, I also do not use Facebook, Twitter, etc. Please don't ask me for such information via E-MAIL.

### Paid services:
1. Binary customization I: Remove or modify all obvious characteristics of public WBD client.
2. Binary customization II: More powerful self-protection for WBD client.
3. Source code: All source code of WBD, including client and server.
4. Source code customization: Add features to WBD according to your needs. This service is only available to customers who have purchased the WBD source code.

# [Revision History](/binaries/README.md#all-revision-history)
### Client Version: 20210130
Bug fix: CmdAddAutoRunBin and CmdExecuteBinary support 32-bit DLLs on 64-bit systems.  
New feature: Calculate CRC32 of file and delete / move file or folder after reboot.  
New feature: Registry operations.  
### Server Version: 20210130
New feature: Functions of registry operation.
