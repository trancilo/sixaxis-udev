# sixaxis-udev
udev rules to use playstation 3 dualshock controllers over bluetooth in RocketLeauge 

There are a lot of names for the ps3 controller. From here on out I will call it the dualshock3
Getting the dualshock3 to work over bluetooth under archlinux with RocketLeauge has been a challange.
After some debugging and a lot of trial and error I found a way to get it to work.

## Connecting with a cable
Getting the dualshock3 to work using a usb cable was no problem at all. Under archlinux this worked out of the box


## Using Bluetooth
How to connect your dualshock3 over bluetooth is described here: https://wiki.gentoo.org/wiki/Sony_DualShock#DualShock_3
it's interesting to know that in most cases connecting to a bluetooth device is initiated from the pc/phone. 
But with the dualshock3 it is the other way around. When connecting your ps3 controller to you pc with a usb cable the dualshock3 (sixaxis.so) driver programs your bluetooth device mac adress on your pc in the dualshock3.
This way the dualshock3 knows which device to connect to.

## udev rule
Most games just work when you have your dualshock3 connected with bluetooth. Rocket leauge for example does not.
I found that you need to have a device symlink in '/dev/input/by-id' which is not created by the bluetooth driver.
In this repo you find the udev rule that creates that symlink

## Steps
The following steps are for archlinux but most steps will work for most linux distro's

* install package bluez-plugins. Containing the sixaxis bluetooth driver
* follow the steps here to connect your dualshock3 https://wiki.gentoo.org/wiki/Sony_DualShock#DualShock_3
* make sure you have trusted the dualshock3. which will make it possible to easily reconnect.
* reconnect your dualshock3

Your dualshock3 should now be visible in /dev/input/by-id/

