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

# Additional tools
- **scanWepNetworks** is simple script that invokes **airodump-ng** command <br />
  to scan only for **WEP encrypted networks** (hit CTRL+C to stop the script)

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

# How it works
It runs 3 processes in a **konsole** windows: <br />
- **aircrack-ng** which is periodically checking if there are any **IVs** collected in **.cap** files
- **aireplay-ng** (option -1) which is used for **fake authentication** so that Access Point thinks you're a client
- **aireplay-ng** (option -3) which is used to **replay ARP packets**, so that Access Point generates new **IVs** that you can capture<br />
  more about <a href="http://www.aircrack-ng.org/doku.php?id=arp-request_reinjection">ARP Request Replay Attack</a>
- script should create directory called **packetsLog** to store all the **.cap** files captured by **airodump-ng**. <br /> After successful crack you can clear it's contents.

# Fragmentation or Chop Chop Attack
I've also written a script that uses **Fragmentation** or **Chop Chop Attack** <br />
You can find it in the same directory, and it's called **fragmentationOrChopChopAttack** <br />
Usage of the script is very similar to the **wepAttack** <br />
```
./fragmentationOrChopChopAttack [BSSID] [CHANNEL] [[CHOP_CHOP_ATTACK]]
```
**[[CHOP_CHOP_ATTACK]]** should be **1** and it means that <a href="http://www.aircrack-ng.org/doku.php?id=korek_chopchop">Korek Chop Chop Attack</a> is gonna be used, <br /> 
if you omit this parameter, or give it value other than **1** than <a href="http://www.aircrack-ng.org/doku.php?id=fragmentation">Fragmentation Attack</a> will be used instead.<br />
Example: <br />
```
./fragmentationOrChopChopAttack AA:BB:CC:DD:EE:FF 11 1 # Korek Chop Chop
./fragmentationOrChopChopAttack AA:BB:CC:DD:EE:FF 11 # Fragmentation Attack 
```
After successful attack script will store **WEP Key** in file **{BSSID_CLEAR}_WEP_KEY_FOUND_LOG**, <br />
where **{BSSID_CLEAR}** is MAC address of the target access point without colons.

# Additional Info
Before you use this script make sure that your script has permissions to execute.<br />
If not type: <br />
```
chmod +x ./wepAttack
```
**REMEMBER** If your first attack fails, and Access Point stops sending **IVs**, don't worry,<br />
you can kill script and try again, because this kind of attack is like a lottery,<br />
the more you try, the bigger win chance you have. **IVs** are generated randomly,<br />
and sometimes you can crack WEP key in first 5000 **IVs**, but sometimes it takes much longer.<br />
<br />
If **WEP network** doesn't have any connected clients attack can fail.<br /> 
So the best moment to attack is when any real client is connected.<br />
You can check this using

# Successfully cracked WEP KEY!
If you manage to crack **WEP key** you should see the following: 
- Aircrack window should output something like
```
KEY FOUND! [ AB:CD:EF:AB:CD:12:34:56:78:90:AB:CD:EF ] 
        Decrypted correctly: 100%
```        
- Script window should output something like:
```
!!!! KEY WAS FOUND !!!!
---------- YOUR WEP KEY IS: ----------------
ABCDEFABCD1234567890ABCDEF
--------------------------------------------
You have it also in file: /root/WEP-Attack/KEY_FOUND_00027255FFC0
```
- There should be also a file like this *KEY_FOUND_00027255FFC0* in current directory



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

