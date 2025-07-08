
DNSmasq


Usally dns on your local machine works in this order.

first it checks the /etc/hosts file for matches 
then if there is no match to goes to you dns server depending on which upstream resolver your using (google,cloudflare,etc...) is specified.
but through out this process there was no caching at all except on your dns server.


dnsmasq is a lightweight DNS server. dnsmasq provides almost all the features a dev needs for DNS management, without having to install a full-blown DNS server, like BIND. Plus, it’s got a lot of features on it and it’s open-source.

dnsmasq accepts DNS queries and either answers them from a small, local, cache or forwards them to a real, recursive, DNS server.

dnsmasq is a DNS query forwarder: it is not capable of recursively answering arbitrary queries starting from the root servers but forwards such queries to a fully recursive upstream DNS server which is typically provided by an ISP.







