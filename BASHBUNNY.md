# Using Bash Bunny

wiki.bashbunny.com
irc.hak5.org

## Setup
3rd position (closest to usb) => arming mode => like flash drive

https://bashbunny.com/setup

Also: Shell access on serial console

Introducing the Bash Bunny - Hak5 2125
https://www.youtube.com/watch?v=CvI_mrQYaF8

DUCKY_LANG ! to set keyboard layout !

### Update

#### Manual
https://wiki.bahbunny.com/#!downloads.md (Downloads page)

=> get tar file, copy to bash bunny

#### Automatic

Now replaced by bash bunny updater tool

### First payload

Copy files from payloads library to payloads/switch1


## TIL

* There are no storage only attacks
* Most attacks require an unlocked account
* Some attacks work on locked PCs - with network device simulation. Those are the advanced ones
* Windows is better supported than Mac which is > Linux
* BadUSB: attack can be implemented in any form factor device ! Not just USB-stick-sized-computers
* can be worm-able
* Thumb drive can detect booting, have OS to boot from... and hide it when system is live (can not be handled by Gnome SW)
* Blocking USB additions when no user is logged in only blocks the network attacks
* Most of the attacks use HID (keyboard)

## Attack scenarios

1) Eliot sneaks into the building, attaches USB device to (unlocked) PC, waits 20 seconds, sneaks out
2) Firmware of USB device is "upgraded" with extra features, victim attaches that himself
3) Attacker can recon first, find USB types being used and use those device IDs...
4) Worms, spreading through USB devices: How reliable is infection ? Maybe not relevant right now

## Error cases where the computer has to still work

1) keyboard is broke (coffee), replace it => keyboard-less verification for newly attached USB devices. Even when screen is locked
2) ...well, as soon as there is a keyboard people can log in and confirm new usb devices....


# Details

## Attack Matrix

||Linux|Mac|Windows|Comment|
|----|-----|---|-------|-|
|PWD stealer|-|X|X|
|Dump and Execute|-|-|X|
|Hack browser/cookies/Beef|X|X|X| (BunnyTap)
|steal Wifi Creds|-|-|X|
|Reverse Shell|X|X|X|
|recon system|-|X|X|
|recon network|X|X|X|nmapper|
|steal files|-|X|X|
|Credential phishing|X|X|X|

Conclusion: BashBunny does not support Linux very well. But many attacks would be as simple as for Windows and Mac....gotta try to write some attacks (for testing and to be there before the bad guys are)

## Payloads

|Stars|Path|Name|OS|Actions|USB devices|Potential Improvements|Comments|
|-----|----|----|--|------------|-----------|-----------------|--------|
||android|fireytv|unlocked android/firetv|enable ADB, install payload, execute|HID, ECM_ETHERNET||
||android|openurl|unlocked android smartphone|open url in browser|HID|
||credentials|BrowserCreds|unlocked Windows|dump plaintext passwords|HID STORAGE, downloads tools||Powershell pwd gatherer: https://raw.githubusercontent.com/sekirkity/BrowserGather/master/BrowserGather.ps1|
||credentials|BruteBunny|unlocked Windows vs routers|brute force local router|HID STORAGE|
|***|credentials|BunnyTap|locked Win/Mac/Lin|hack browser|RNDIS_ETHERNET/ECM_ETHERNET||uses DNSSpoof, https://samy.pl/poisontap/|
|**|credentials|DumpCreds|locked ? Windows 10|pwd stealer|HID,RNDIS_ETHERNET, RNDIS_ETHERNET STORAGE||impacket tools, mimikatz, powerdump|
||credentials|JackRabbit|unlocked Windows|pwd stealer|HID STORAGE||mimikatz|
||credentials|macinfograbber|unlocked Mac|cred stealer|HID STORAGE|||
||credentials|MrRobot|unlocked Windows|cred stealer|HID, RNDIS_ETHERNET||mimikatz/mimidogz|
|*|credentials|PasswordGrabber|unlocked Windows|pwd grabber|HID STORAGE||https://github.com/AlessandroZ/LaZagne (Pony style)|
|**|credentials|QuickCreds|locked/unlocked Win/Mac/Lin||RNDIS_ETHERNET,ECM_ETHERNET ||responder required|
||credentials|SudoBackdoor|unlocked Mac/Lin||ECM_ETHERNET HID||second visit to loot|
||credentials|WifiCreds|unlocked Windows|Steals Wifi Creds|HID STORAGE|||
||credentials|WifiGrabber|unlocked Windows|Steals Wifi Creds|HID STORAGE|||
||credentials|WifiPass|unlocked Windows||HID STORAGE|||
||credentials|WindowsCookies|unlocked Windows |gets facebook session cookies|HID, RNDIS_ETHERNET|||
||credentials|WiPassDump|unlocked Windows|gets Wifi pwds|HID STORAGE|||
||execution|exe_UACBypassD&E|unlocked Windows|download and execute file|HID STORAGE|||
||execution|psh_DownloadExec|unlocked Windows|dl & exe|RNDIS_ETHERNET HID|||
||execution|psh_DownloadExecsSMB|unlocked Windows|dl & exe from SMB server|RNDIS_ETHERNET HID||impacket|
||execution|RAZ_VBScript|unlocked Windows|executes vbscript|HID STORAGE|||
||execution|RevShellBack|unlocked Windows|start reverse shell|RNDIS_ETHERNET HID|||
|*|execution|ShellExec|unlocked Mac/Lin|Beef hooking|ECM_ETHERNET HID VID_0X05AC PID_0X021E|||
||execution|StickyBunny|unlocked Windows|allows admin login|HID|||
||exfiltration|BlackBackup|unlocked Windows|Wlan/Logon credentials|HID STORAGE|||
||exfiltration|BrowserData|unlocked Windows|browser history/bookmarks|HID STORAGE|||
||exfiltration|FileInfoExfil|unlocked Windows|steal files matching a pattern|HID STORAGE|||
||exfiltration|ftp_exfiltrator|unlocked Windows|exfil files to FTP|HID STORAGE|||
||exfiltration|MacPDFExfil|unlocked Mac|steal PDFs to Storage|STORAGE HID VID_0X05AC PID_0X021E|||
||exfiltration|Powershell_TCP_Extractor|unlocked Windows|steals data and sends to server|HID STORAGE|||
||exfiltration|SmacAndGrab|unlocked Mac|steal list of files to storage|STORAGE HID VID_0X05AC PID_0X021E|||
||exfiltration|smb_exfiltrator|unlocked Windows|exfiltrate files by SMB|HID, RNDIS_ETHERNET ||impacket|
||exfiltration|usb_exfiltrator|unlocked Windows|exfiltrate files to Storage|HID STORAGE|||
|**|exploitation|Metasploit-Autopwn|locked/unlocked Windows vs. network|run autopwn vs network connected client|RNDIS_ETHERNET||metasploit|
||general|dryClean|BB|clean loot directory||||
||general|DuckyTemplate|BB|run ducky scripts on BB||||
||general|ExecutableInstaller|unlocked Windows|copy and start executable|HID STORAGE|||
||general|GitBunnyGit|BB|update BB||||
||general|InfiniteControl|unlocked all|keep hitting CTRL|HID|||
||general|Proxy_Interceptor|unlocked Windows|import certificate to Windows|HID STORAGE|||
||general|Windows_NIC_Sharing|unlocked Windows|setup networking for BB<->Windows|HID|||
||Incident_Response|Hidden_Images|unlocked Windows|file magic finds image files|HID STORAGE|||
||Incident_Response|Link_File_analysis|unlocked Windows|find strange lnk files|HID STORAGE|||
||phishing|Captiveportal|active user Windows/Mac/Linux|fake captive portal to phish credentials|RNDIS_ETHERNET/ECM_ETHERNET|||
||phishing|dns_poisoning_mac|unlocked mac|modifies hosts file|HID|||
||phishing|Local_DNS_Poisoning|unlocked windows|modifies hosts file|HID|||
||phishing|MacPhish|active user mac|create fake ui to phish root pwd|HID STORAGE|||
||prank|90sMode|Unlocked Windows|sets screen resolution|HID STORAGE|||
|* 1|prank|Ascii-Prank||displays ascii image|STORAGE HID VID_0X05AC PID_0X021E|||
||prank|Bunny-Flip|unlocked Windows|flips screen|HID|||
||prank|lockpc|unlocked lin/win/mac|writes lock tips|RNDIS_ETHERNET,ECM_ETHERNET, HID, HID VID_0x05AC PID_0x021E|||
||prank|MacDesktop|unlocked mac|sets background|HID STORAGE 0xF000/0xFF02|||
|* 1)|prank|NotepadFun|unlocked Windows|writes warning to notepad|HID|||
||prank|Photo Booth Ugly Prank|unlocked Mac|takes photo and insults|HID VID_0X05AC PID_0X021E|||
||prank|RAZ_ThemeChanger|unlocked Windows|sets windows theme|HID STORAGE|||
||prank|Rickroll|unlocked Windows|HID, RNDIS_ETHERNET||||
||prank|Unified RickRoll|unlocked Mac|display rickroll|HID VID_0X05AC PID_0X021E|||
||prank|Unified RickRoll Windows|unlocked Windows|display rickroll|HID VID_0X05AC PID_0X021E|||
||prank|win93|unlocked lin/mac/win|open browser and nmap scan|ECM_ETHERNET, RNDIS_ETHERNET, HID|||
||recon|InfoGrabber|unlocked Windows|grab system info|HID STORAGE|||
||recon|Link_File_analysis|unlocked Windows|get lnk file data|HID STORAGE|||
||recon|MacGetUser|unlocked mac|list mac users|HID VID_0X05AC PID_0X021E STORAGE|||
|*2|recon|MacProfiler|unlocked mac|exfiltrate system info||||
|*1|recon|nmapper|win/lin/mac|scan target with nmap|RNDIS_ETHERNET, ECM_ETHERNET|||
||recon|PrivEscChecker|unlocked windows|check windows boxes for privilege escalation vuls|HID STORAGE|||
||recon|ProcessInfo|unlocked windows|return all running processes|HID STORAGE|||
||recon|rdp_checker|windows|check if rdp is enabled on target|RNDIS_ETHERNET, ECM_ETHERNET||impacket|
|*1|remote access|LinuxReverseShell|unlocked Linux|start reverse shell|HID STORAGE|||
|*3|remote access|MacReverseShell|unlocked mac|python reverse shell|HID VID_0X05AC PID_0X021E|||
||remote access|NothingLess|unlocked windows| shares foilder |HID STORAGE|||
||remote access|RAZ_MacReverseShell|unlocked mac|bash persistent reverse shell|HID|||
||remote access|RAZ_ReverseShell|unlocked windows|nc reverse shell|HID STORAGE|||
|**2|remote access|SingleSecondShell|unlocked windows|metasploit reverse shell|HID STORAGE||metasploit/armitage|
| 2 ?|remote access|UndercoverBunny|unlocked windows|creates wifi network|HID|||
||remote access|USB_Intruder|unlocked windows|in depth infection + meterpreter reverse shell|HID STORAGE||metasploit|
||remote access|WindowsMeterpreterStaged|unlocked windows|download and exectute meterpreter|HID||metasploit|
||remote access|Win_x64_JS_Rev_Meter|unlocked windows|js meterpreter|HID||metasploit|
||sFTP Directory Grabber||unlocked windows|data exfiltration by ftp|HID STORAGE|||


1) Good for testing, because simple
2) replicate something like that for Linux as POC attack
3) Check if it can be used on linux

Stars:
* complex attacks
* vs. Linux
* Things that worked logged in / without login

These are the criteria for the stars.



### Empire Framework

https://pentestit.de/osx-persistent-backdoor-mit-empire-framework/

TODO


# Sources for Bash Bunny
## Youtube

Bash Bunny Primer - Hak5 2225
https://www.youtube.com/watch?v=8j6hrjSrJaM

The Bash Bunny 1990's Prank - Hak5 2226
https://www.youtube.com/watch?v=Ei6YhehET3Y

Password Grabber Bash Bunny Payload - Hak5 2305
https://www.youtube.com/watch?v=LtqsKftRFiw

# BadUSB and similar

## BadUSB

By Karsten Nohl and Jakob Lell

https://opensource.srlabs.de/projects/badusb

Blackhat USA 2014: https://www.youtube.com/watch?v=nuruzFqMgIw
