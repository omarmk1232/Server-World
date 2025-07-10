# BIND (Berkeley Internet Name Domain)

BIND to keep it simple is a DNS server with much more configuration options than dnsmasq.

and to understand how it works and how to configure it lets first take a quick look on how DNS works.

## DNS

DNS is a distributed, hierarchical system that manages the mapping between domain names and IP addresses

dns server structure works like a tree consisting of multiple servers

starting first with authoritive servers these are server that host the records of each domain 

from the root servers (.) ---> TLD Servers (.com) ---> SLD (example.com) ---> Subdomains (www.example.com)

these are authoritve servers they only host the records.

then we have Recursive Resolver Servers that query the authoritve servers for answers.

example for resovlers : google and cloudflare

**ZONE** A zone is the part of the DNS namespace that you manage as a single administrative unit, stored in a zone file on your authoritative server its where you host you domains and records.


## BIND

DNS server software, originally developed at UC Berkeley, that implements the DNS protocols to translate domain names into IP addresses. It acts as an authoritative name server, storing DNS zones and records, and can also function as a recursive resolver to perform lookups on behalf of clients.

for more information visiting [BIND Documentation](https://bind9.readthedocs.io)


