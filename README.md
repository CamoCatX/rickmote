rickmote
========

## The Rickmote Controller: Hijack TVs using Google Chromecast
![The Rickmote Controller](docs/Rickmote.jpg)

The Rickmote is a Python program for Hijacking Chromecasts and playing arbitrary video to their connected TVs. Full details on how the hack works will be provided at the talk "Rickrolling your Neighbors with Google Chromecast" at HOPE X in New York. See you there!

Additionally, this is all streamlined into a Raspberry Pi (pictured above) with details to come soon at BlackHat USA 2014's Tools Arsenal! If you just can't wait and want to try pranking your friends right away, here are the vital ingredients:

##### Software Dependencies: 
* aircrack-ng
* Tkinter python library (python-tk in debian)
* hostapd
* dnsmasq
* Network Manager, specifically nmcli

##### 3D Printed Case:
Download the 3D models for the slick Rickmote 3D printed case here at Thingiverse
http://www.thingiverse.com/thing:398100
##### Hardware Recommended by Original Developer 
###### *not me!*
* [Raspberry Pi Model B Revision 2.0](https://www.amazon.com/Portable-Raspberry-Revision-Components-Electronic/dp/B00LJPJIGC/ref=sr_1_2?keywords=Raspberry+Pi+Model+B+Revision+2.0+%28512MB%29%29&sr=8-2)
* [Samsung 32GB PRO SDHC](https://www.amazon.com/Samsung-Class-Adapter-MB-MD32GA-AM/dp/B07169Y2VP/ref=sr_1_4?keywords=Samsung+32GB+PRO+SDHC&sr=8-4) 
* [2.8" Touchscreen Display for Raspberry Pi](https://www.adafruit.com/product/1601)
* [AmazonBasics High-Speed HDMI Cable](https://www.amazon.com/AmazonBasics-High-Speed-HDMI-Cable-1-Pack/dp/B014I8SSD0/ref=sr_1_3?keywords=AmazonBasics%2BHigh-Speed%2BHDMI%2BCable%2B(6.5%2BFeet%2F2.0%2BMeters)&sr=8-3&th=1)
* [Lithium Ion Polymer Battery - 3.7v 2500mAh](https://www.adafruit.com/product/328)
* [Motorola Micro USB Charger (5V, 850mA) Model: SPN5504](https://www.amazon.com/Motorola-SPN5504-Original-Charger-Detachable/dp/B007BYEY0K/ref=sr_1_4?keywords=Motorola+Micro+USB+Charger+%285V%2C+850mA%29+Model%3A+SPN5504&sr=8-4)



##### Setup Assumptions:
The Rickmote Controller needs to pull a lot of Wi-Fi shenanigans in order to automate the hack. For best results, you may want to try using Kali Linux as it has the easiest setup for wireless drivers that support injection. Also note that we are actively working on reducing these assumptions! Sorry it's so specific in the meantime.
* Three wireless interfaces.
    * wlan0 is a client interface that is set to Managed mode
    * mon0 is a monitor mode interface that supports packet injection
    * wlan1 is a an AP that is set to Master mode
* wlan1 is an access point to an open AP named "RickmoteController", using hostapd
* wlan1 has an IP of 192.168.75.1, netmask 255.255.255.0
* A working Internet connection, bridged to wlan1
    * Tethering to a smart phone tends to be a decent method
    * We currently only have support for playing YouTube videos from the real Internet
* It is also worth noting that the current Rickmote de-authenticates every wireless network it sees, and is generally very rude

#### More Information
For more information, [try here](https://www.youtube.com/watch?v=dQw4w9WgXcQ).
#### TODO: Create docker container for access without raspberry

#### Notes (CY)
How the procedures work for Hijacking Chromecast:
_______________________________________
* 1: Deauth the STA connectivity of Chromecast to the WiFi AP. 
________________________________________
* 2: Connect to the AP mode of Chromecast, usually set as "Network Name"
__________________________________________
* 3: HTTP POST to set the Chromecast to the AP setup for hijacking purpose
__________________________________________
* 4: Find Chromecast using upnp protocol using multicast address (not working certain times) 
__________________________________________
* 5: Enable the Youtube apps
_________________________________________
