A *Site-to-Site Virtual Private Network* is a type of [[VPN]] that is used to connect entire networks to one another. Usually, the implementation consists of creating a VPN tunnel from a border router from a site to another border router on another site.

## IPSec

IPSec is a site-to-site VPN technology that **encrypts IP packets and payloads before sending** them to a VPN tunnel. This grants security to the communication, even over the public internet. When using an IPSec tunnel, a router will:

1. Encrypt any traffic that is directed to the other side of the VPN tunnel. For example, when a communication needs to happen between a PC on a site and a [[Servers|server]] on the other site;
	1. This encryption is done from layer 3 packet and above. So information about source and destination [[IPv4 Addressing|IP address]], DSCP, TCP/UDP ports, payload, etc will be encrypted;
2. The border device will then append a VPN header and an IP header to this encrypted information and forward it to the tunnel;
3. On the other side of the tunnel, the other border device will receive the IPSec packet, de-encrypt it and forward it to the local network.

IPSec only supports unicast packets, so layer 3 multicast and broadcast packets will not be forwarded through the tunnel (making the usage of technologies like OSPF impossible over IPSec). However, this can be accomplished by using **GRE over IPSec** (*Generic Routing Encapsulation over IPSec*). GRE encapsulates the IP packets with a GRE header and IP header, and then IPSec further encapsulates this payload with a VPN header and IP header, to forward it through the tunnel.

![[IPSec Packet.png]]

