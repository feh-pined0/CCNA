*Address Overload* or PAT (*Port Address Translation*) is a method to translate multiple addresses to a single public IP address, by using the source layer 4 port as a tool.

The method consists of translating multiple source addresses to the same public IP, **but assigning a different source port** to the packet. This way, even if the replies to those packets arrive with the same destination IP, the router could distinguish which packet is for which host, based on that generated port number.

Refer to this example:

![[NAT Overload Example.png]]

> If `PC1` and `PC2` selected the same random source port, `R1` would generate a different port to one of the two packets and append that to the translated address, so that both packets have different port addresses and could be distinguished from each other, even when using the same IP address.

