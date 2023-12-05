*Network Address Translation* is a layer 3 (network/internet) standard. It translates and rewrites layer 3 IP addresses and layer 4 (transport) ports. This translation can be from multiple IPs to one (generally private [[IPv4 Addressing|IPv4]] addresses to a single, [[Private Addresses|public IP address]]) or multiple to multiple (when the NAT protocol has a pool of outbound addresses it can assign).

There are multiple [[Types of NAT|types of NAT]], which can be used depending on the case. The most common use for NAT is for translating a private IPv4 address to a public one.

For the purposes of translation, NAT defines some terms to differentiate types of IPs (refer to the image):

![[NAT Inside & Outside Networks.png]]

- **Inside Local**: the IP of a host on the inside network from the "perspective" of an inside interface (in this example, R1's `192.168.0.1` interface).
	- In this example, one inside local address would be `192.168.0.167` (PC1 interface);
- **Inside Global**: the IP of a host on the inside network from the "perspective" of an **outside** host (basically, the IP address of this inside host as seen by an outside host);
	- In this example, if a NAT is configured to translate to `203.0.113.1`, this address would be an inside global address;
- **Outside Local**: the IP address of an outside host from the "perspective" of an inside interface.
	- In this example, `8.8.8.8` is an outside local address;
- **Outside Global**: the IP address of an outside host from the "perspective" of an outside interface.
	- In this example, `8.8.8.8` is also an outside global address. This is because no translation from outside -> inside is occurring. If it was, then this outside host would have an IP on the outside network (**outside global**) and a different IP on the local network (**outside local**);