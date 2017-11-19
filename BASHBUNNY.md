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

## Payloads

|Stars|Path|Name|OS|Actions|USB devices|Potential Improvements|Comments|
|-----|----|----|--|------------|-----------|-----------------|--------|
||android|fireytv|unlocked android/firetv|enable ADB, install payload, execute|HID, ECM_ETHERNET||
||android|openurl|unlocked android smartphone|open url in browser|HID|
||credentials|BrowserCreds|unlocked Windows|dump plaintext passwords|HID STORAGE, downloads tools||Powershell pwd gatherer: https://raw.githubusercontent.com/sekirkity/BrowserGather/master/BrowserGather.ps1|
||credentials|BruteBunny|unlocked Windows vs routers|brute force local router|HID STORAGE|
|***|credentials|BunnyTap|locked Win/Mac/Lin|hack browser|RNDIS_ETHERNET/ECM_ETHERNET||uses DNSSpoof, https://samy.pl/poisontap/|
|**|credentials|DumpCreds|locked ? Windows 10|pwd stealer|HID,RNDIS_ETHERNET, RNDIS_ETHERNET STORAGE||impacket tools, mimikatz, powerdump|
||credentials|JackRabbit|Windows|pwd stealer|HID STORAGE||mimikatz|
||credentials|macinfograbber|Mac|cred stealer|HID STORAGE|||
||credentials|MrRobot|Windows|cred stealer|HID, RNDIS_ETHERNET||mimikatz/mimidogz|
|*|credentials|PasswordGrabber|Windows|pwd grabber|HID STORAGE||https://github.com/AlessandroZ/LaZagne (Pony style)|
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
||exfiltration|BlackBackup||||||
||exfiltration|browserData||||||
||exfiltration|FileInfoExfil||||||
||exfiltration|ftp_exfiltrator||||||
||exfiltration|MacPDFExfil||||||
||exfiltration|Powershell_TCP_Extractor||||||
||exfiltration|SmacAndGrab||||||
||exfiltration|smb_exfiltrator||||||
||exfiltration|usb_exfiltrator||||||
|||||||||
|||||||||
|||||||||





Stars: I am working on Linux, Windows only attacks will get less stars


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
