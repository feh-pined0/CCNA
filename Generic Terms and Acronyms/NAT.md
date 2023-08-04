*Network Address Translation* is a layer 3 (network/internet) protocol. It translates and rewrites layer 3 IP addresses and layer 4 (transport) ports. This translation can be from multiple IPs to one (generally private [[IPv4 Addressing|IPv4]] addresses to a single, [[Private Addresses|public IP address]]) or multiple to multiple (when the NAT protocol has a pool of outbound addresses it can assign).

NAT also appends a new port to the packet's source port field so it can track which packets should be translated back to the original form when a response arrive, should it arrive.