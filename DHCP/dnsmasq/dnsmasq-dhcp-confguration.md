
# Dnsmasq Conifuration As A DHCP Server

this tutorial explains how to deploy an dhcp server using dnsmasq and configure a dhcp range pool
for it to lease from as will as the [options](https://blog.abysm.org/2020/06/human-readable-dhcp-options-for-dnsmasq/) it can send to the host with the ip like dns,ntp,and gateway.

---

## 📋 Prerequisites

- A Linux server in my case i am using rhel
- Root or sudo access
- Basic understanding of editing config files
- two servers one as a dhcp-server and another one for testing 
---


## Installation

```bash
sudo dnf install dnsmasq
```

## Setup

```bash
#first we need to configure dnsmasq to work as a dhcp server by editing /etc/dnsmasq.conf file

vim /etc/dnsmasq.conf

#okay first we need to configure the ip range the dhcp server can lease ip from 
#in my case i cant disable my the dhcp in my router so i have to make sure that their is no conflict between the ranges between the router #and the my dhcp server.

dhcp-range=192.168.3.200,192.168.3.220,12h #ip range from 200 to 220 lease time 12h

#dhcp options 
#dhcp-option=$option-number,$option value
#for example this is an option for default route
dhcp-option=3,192.168.3.93

#you can bind a specific to a specific mac address 
#example
dhcp-host=AA:BB:CC:DD:EE:FF,192.168.1.210


```
## testing

when a new host joins the network it sends a broadcast DHCP discovery request on port 67 on the network.
and since i have two dhcp server(one from the router and server 1 (192.168.3.93)) then the  new host will take the first dhcp offer it can get.

since i cant disable the router dhcp i had to try multiple times to get an offer from server dhcp server.


```bash

#once you are done configuring the dhcp server (server 1 192.168.3.93)
#make sure that server 1 port 67 on UDP is open and that the firewall allows inbound access to dhcp

ss -tuln
#you should see an entry for 0.0.0.0:67
firewall-cmd --list-services #look for dhcp if not found add it
firewall-cmd add-service=dhcp

#restart server 2 and check if it takes an new ip from our defined range
ip addr

#to check if my dhcp server gave the other server an offer 
journalctl -u dnsmasq # you will see in the log that server gave an DHCPoffer to server 2 with the new ip from our range


```bash

images














