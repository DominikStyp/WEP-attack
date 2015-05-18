# WEP Attack

# What is this ?
Extremly simple script that can be used to **crack WEP network password**.<br />

# How to use ?
All you have to do is type following command:
```
./wepAttack [BSSID] [CHANNEL] [[SPOOFED_MAC]]
```
**Options explanation:**
- [BSSID] is MAC address of the target
- [CHANNEL] is the network channel
- [[SPOOFED_MAC]] is the MAC address that you want to use to change your WiFi card original MAC address (this is optional)<br />
  last option is used to hide your activity 

# Examples
Without spoofed MAC (**original MAC** of your card is used): <br />
```
./wepAttack AA:BB:CC:DD:EE:FF 11
```
**Spoofed MAC** will be used. **macchanger** will change your card's MAC to 00:11:33:44:55:66 <br />
```
./wepAttack AA:BB:CC:DD:EE:FF 11 00:11:33:44:55:66
```

# Dependencies
**Following script IS NOT dependent on any library, nor external sources.**<br />

# Requirements
- Wireless adapter which supports injection (see [https://code.google.com/p/reaver-wps/wiki/SupportedWirelessDrivers Reaver Wiki])
- Linux Backtrack 5 
- Root access on your system (otherwise some things may not work)
- AND if you use other Linux distribution
  - Reaver 1.4 (I didn't try it with previous versions)
  - KDE (unless you'll change 'konsole' invocations to 'screen', 'gnome-terminal' or something like that... this is easy)
  - Gawk (Gnu AWK)
  - Macchanger
  - Airmon-ng, Airodump-ng, Aireplay-ng
  - Wash (WPS Service Scanner)
  - Perl

# Additional Info
Before you use this script make sure that your script has permissions to execute.<br />
If not type: <br />
```
chmod +x ./wepAttack
```

# DONATIONS
Like my project ?   
Want to help in future development, and adding new features ?   
If you find this project useful...  
#### You can <a href="https://sites.google.com/site/dominikdonationbutton/">SUPPORT ME BY PAYPAL</a>
I created PayPal Donation Button as Google Site because here not all HTML tags are allowed and Donation Button HTML can't be put here...  
Every dollar will be appreciated and help me in future development of my projects. 

# Legal Disclaimer
Usage of **WEP Attack** for attacking targets without prior mutual consent is illegal.  
It is the end user's responsibility to obey all applicable local, state and federal laws.  
Developers assume no liability and are not responsible for any misuse or damage caused by this program.

