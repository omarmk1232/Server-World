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

###
first specify from  which file dnsmasq will resolv local domains in my case i left it on default /etc/hosts
but you can change it or add some domains explicitly in the config.

local=/etc/hosts

### 




