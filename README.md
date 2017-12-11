# Bash Bunny plan

Create a linux tool to protect linux agains a bash bunny.

## TODO

- Create generic network Attackmode
- create several linux attack scripts as POC
- Identify attached USB devices on plugin
- Define logic how to handle those

## Existing projects

### USBGuard

USBGuard:
https://dkopecek.github.io/usbguard/

(just knows black and white)

### USBGuard GNOME

https://github.com/k00n/usbguard-gnome
(Muelli pointed me there)
A Gnome GUI for USB Guard (which is in the Ubuntu repo but bot very smart)

Detailed description (German):
https://www.privacy-handbuch.de/handbuch_91a.htm

Translation (short):

Install: ```sudo apt install usbguard```
Init whitelist (plug in ALL your USB devices for that):
```
sudo usbguard generate-policy > rules.conf
sudo cp rules.conf /etc/usbguard/rules.conf
sudo chmod 0600 /etc/usbguard/rules.conf
```
Modify */etc/usbguard/usbguard-daemon.conf*:
```
PresentDevicePolicy=apply-policy
PresentControllerPolicy=apply-policy
```
(About how to handle the boot up situation. With this setting policy applies to boot up connected devices)


### Other

USB inhibitor:
https://georgemuraruc.wordpress.com/2015/08/25/the-usb-inhibitor/
https://georgemuraruc.wordpress.com/2015/08/03/how-the-system-deals-with-usb-devices/
https://github.com/murarugeorgec/USB-checking


## Relates (and open) PRs everywhere:

### Bash Bunny

https://github.com/hak5/bashbunny-payloads/pull/298
