*Domain Name System* is a layer 7 (application) protocol that "resolves" (converts) human-readable domain names into [[IPv4 Addressing|IP]] addresses for applications to use. It works in a client-server style, as clients perform queries for different types of names.

Here is an example of a DNS query:

![[Pasted image 20231101204818.png]]

It is not common to have a DNS server on the LAN. Usually, [[DHCP|DHCP servers]] will advertise DNS servers that reside somewhere on the WAN (such as public DNS servers, like google's `8.8.8.8`).

The DNS protocol uses TCP and UDP port 53. UDP is used on most cases, while **TCP is used when DNS messages surpass a 512 byte threshold**.