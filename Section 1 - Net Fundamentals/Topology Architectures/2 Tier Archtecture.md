Cisco defines some architectures to build networks based on specific needs, and these usually target redundancy of devices and minimizing single points-of-failure. Based on these premises the 2 tier architecture provides 2 layers of network fabric: the **access layer** and the **distribution layer**.

The access layer provides network access to endpoints on the network, such as computers, servers and phones, for example. This is usually done by providing layer 2 switches to which these [[Endpoints|endpoints]] can connect. From this, the [[Switches|switching]] fabric can provide layer 2 functions like MAC-address forwarding and port-security. These switches **do not** connect to each other (this technique is called “switch daisy-chaining”), as this could cause single points of failure or unnecessary redundancy. Instead, they are connected to the next layer’s (distribution layer) layer 3 switches.

The distribution layer is responsible for distributing (bruh) the packets in the network. This means that all packets traveling within the LAN, or from the LAN to outside wan goes through here. Generally, this layer does the majority of the [[Routers|routing]] for the LAN, such as VLAN-routing or default gateway routes. It’s also common to implement ACLs, packet inspection and general [[NGFW and IPS (Firewall)|firewall]] stuff on this layer.

The distribution layer is then connected to the LAN edge (usually a router, or two for redundancy) for outbound traffic. The following image illustrates a 2 tier network:

![](https://lh6.googleusercontent.com/LW1CcLSGD4wxNgV7V0_yC36oXTpAREqWEGp0ZztTgbLhU6HEPe5yeqPCj8p86w1kBOtSh1mbfxTkQ5N6UpVnYTmiHc5OQ25wYX5m2R0-CtSXo-zj12K7Tr1PvqBYp77incC2XOZFA7YsEhlFDV4Y_n4)

Switches on the access layer form a connection to each distribution layer switch, and distribution layer switches form a connection to each other to perform [[First-Hop Redundancy|first-hop redundancy]].