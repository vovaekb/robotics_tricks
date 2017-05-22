# Common issues happen when using ROS and Raspberry Pi

## eth0 interface is missing in ifconfig on Ubuntu
Set an IP address for Raspberry Pi by adding 'ip = 192.168.0.4' at the end of cmdline.txt
Do that using the command:
```
sudo nano /boot/cmdline.txt
```
Make sure you add nothing else, not even a space or a return. After that, reboot your Raspberry Pi and type hostname -I to see if the IP address is set.

## eth0 interface is setup statically
Problem: in ifconfig Ip address is set to 192.168.x.x - statically

In file /etc/network/interfaces should be line:
```
iface eth0 inet dhcp
```
Restart network interface:
```
sudo ifdown eth0 && sudo ifup eth0
```
