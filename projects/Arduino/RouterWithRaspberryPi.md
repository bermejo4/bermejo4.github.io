---
layout: post
title: Router with a Raspberry Pi
---
*****
Is very easy turn your Raspberry into a router or an access point.  
In some tutorials (that in many cases they didn't work), they change configuration files from raspberry to transform your raspberry into
a router, but in my case I use a software (RaspAp) that is installed with some configuration questions and in few minutes is working.
It's true that if the tutorial that overwite some files and change totally other works, our router will be more configurable, but the 
option that I choose is very configurable too and incorporate a graphical user interface to make the experience more comfortable.  

You only have to open the terminal and write the following:
* First commands are to update the raspberry:
````bash
sudo apt-get update
sudo apt-get full-upgrade
sudo reboot
````

* Once everything is updated we open again the terminal after the reboot and write: 
````bash
curl -sL https://install.raspap.com | bash
````


Is very important to have more than one network interface, for example, eth0 to internet input, and wlan0 to the other network that 
we are creating. Or we can add other internet interface, for example wlan1, inserting a network interface controller in one usb port of 
our raspberry.

After the RaspAp installation conclude we open internet and write: localhost  
A small window will be opened asking user and password. You have to write:
* User: admin
* Password: secret  
After that the graphical user interface is opened, and to configure an access point you have to go to "Hotspot" menu in the left-side bar.
  
Configure the following:  

In "Basic settings":
- Interface: wlan0
- SSID: "Introduce the name that you want for your network, for example RaspNetwork"
- Wireless Mode: 802.11g-2.4 GHz, (Depend on what you want you can change it)
- Channel: 1

In "Security":
- Security type: "WPA2"
- Encryption type: "CCMP"
- PSK: "Here introduce the password that you want for your network"

In "Advanced":
- Bridged AP mode: ON
- WiFi client AP mode: ON

Once everything were configurated click in "Save settings".

If something doesn't work reboot the Raspberry and revise the steps.  
For more documentation visit the official website of RaspAp.
