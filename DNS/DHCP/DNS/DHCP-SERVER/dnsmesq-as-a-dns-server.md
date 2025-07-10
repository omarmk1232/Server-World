# Setup a DNS Server with dnsmasq

This guide explains how to set up `dnsmasq` as a lightweight caching DNS server on Linux.

---

## 📋 Prerequisites

- A Linux server in my case i am using rhel
- Root or sudo access
- Basic understanding of editing config files
- two servers one as a dns-server and another one for testing 
---

##  Installation

```bash
sudo 
sudo dnf install dnsmsq

 ```

## Setup

you can find the configuration file for dnsmasq in /etc/dnsmasq.conf

in my case i want server one(192.168.3.93) where i installed dnsmasq to be my dns server 
and server 2 will use this server to query for domains

```bash
#first specify from  which file dnsmasq will resolv local domains in my case i left it on default /etc/hosts
#but you can change it or add some domains explicitly in the config.

local=/etc/hosts

listne-address=192.168.3.93,127.0.0.1 #addresses on which will the dnsmasq server listen

#by default if the domain is not in the local hosts it will query the nameservers on regesterd on the server for it
#or you can explicitly define you upstream servers
server=8.8.8.8 # this takes precedance over /etc/resolv.conf

#you can find them in /etc/resolv.conf

#make sure to start and enable dnsmasq on the server after your done with the setup or any change with the setup
systemctl enable --now dnsmasq
systemctl status dnsmasq

```
### now we need to make sure that our server is listening on 192.168.3.93 port 53 and that the firewall allows inbound traffic to this port

```bash

ss -tuln # check if 192.168.3.93:53 and 127.0.0.1:53 are open

firewall-cmd list-servcies #check if dns service is enabled

#if not add it
firewalld-cmd add-service=dns

```

now on your dns-server (server 1) change your dns server to your localhost (dnsmasq)

i used nmtui for simplicity and changed the dns server on my connection to 127.0.0.1
and now dnsmasq is my default dns server all dns query will go through it

for server 2 do the same change your dns server ip to point to server 1 (192.168.3.93)
so now server 2 first will check its local domains then it will query server 1 if he cant find the domain 

to test the setup:

```bash
#add a local domain on /etc/hosts on server 1
vim /etc/hosts
#and add
222.222.222.222 google.com

#now if query google.com from server 1 or 2 you will get 222.222.222.222
nslookup google.com

#the output
Server:         192.168.3.93
Address:        192.168.3.93#53

Non-authoritative answer:
Name:   google.com
Address: 222.222.222.222
Name:   google.com
Address: 2a00:1450:4006:810::200e

```





