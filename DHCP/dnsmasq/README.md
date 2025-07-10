# DHCP (Dynamic Host Configuration Protocol)

DHCP is a network protocol that automates the assignment of IP addresses and other network configuration parameters to devices on a network. It simplifies network management by dynamically assigning these settings, eliminating the need for manual configuration of each device.

## how DHCP works

**Step 1**:DHCPDiscover

when a device is added to the network it sends a broadcast request on the network looking for hte dhcp server

**Step 2**:DHCPOffer

the dhcp server sends an available ip from the pool to the host as an offer.

**Step 3**:DHCPRequest

the host accepts the host and sends a reuqest to the dhcp server.

**Step 4**:DHCPAck

the dhcp server acknoldges the hosts reqests and reserves this ip for it.



>[!note]
> dhcp uses UDP to communicate ports 67 & 68.
> dhcp sends other info with the ip to the host like dns,gateway,ntp these are called [options](https://blog.abysm.org/2020/06/human-readable-dhcp-options-for-dnsmasq/)



