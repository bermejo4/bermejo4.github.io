---
layout: post
title: Static Ip Address in a Raspberry for IoT
---
*****
If we are developing an IoT project with a Raspberry Pi, is recommended to set one of the interfaces as the interface which is going to
comunicate with the other IoT devices of our Iot Network. This interface might have always the same IP; to do that we have to modify a
configuration file of the Raspberry.  

It's important to say that I am working with Raspbian Operating System.  

The reason because the interface might have the same Ip is very easy. If we have a dynamic Ip it can be changed every time that the DHCP
protocol of our router wants, but if we put a Static IP the IP will be always the same, so our IoT devices, that actuate as clients
in a client-server relation, being the raspberry the server, can find the server at the same IP address. 

Somebody can say that this problem can be solved putting the hostname of the server instead of IP address. Yes it is true. 
But some IoT devices haven't got the MDNS protocol, so they can't solve hostnames as IPs.

This process is very easy.
* Open a terminal into the raspberry and write:
````bash
cp /etc/dhcpcd.conf /etc/dhcpcd.conf.orig
````
This command has created a copy of the file that we are going to modify, adding .orig to identify that is the original file.
This is important just in case we have modified something unintentionally and after we want back to the original configuration slving the problem.

* After this security step, we have to write into the terminal:
````bash
sudo nano /etc/dhcpcd.conf
````
The file is open.
* At the end of the file we have to write the following:
````bash
interface eth0
static ip_address=192.168.0.100/24
static routers=192.168.0.1
static domain_name_servers=192.168.0.1
````
Being "192.168.0.100" the Static IP that we want for our Raspberry, "/24" the mask of our network and 192.168.0.1 the gateway.
For save the changes type: "ctrl+o", type "enter" and "ctrl+x".

* Finally write into the terminal:
````bash
sudo reboot
````
* When the process has finished and the Raspberry has been rebooted, open a terminal and write:
````bash
ifconfig eth0
````
You can observe in "inet" the Ip that you choose.
