As [[Routers|routers]] add multiple routes to their routing tables, packets can match multiple routes and thus the router needs to select one to use. This selection is based on the **most specific route**.

For example, given this routing table:

```IOS
R1# show ip route
Gateway of last resort is not set
192.168.1.0/24 is variably subnetted, 2 subnets, 2 masks
   C 192.168.1.0/24 is directly connected, GigabitEthernet0/0
   L 192.168.1.1/32 is directly connected, GigabitEthernet0/0
```

- If a packet for destination `192.168.1.57` arrives at this device, it will choose the [[Routing Protocol Codes|connected route]] to forward the packet, because it is the only match;
- If a packet for destination `192.168.1.1` arrives at this device, it will choose the local route because, although both routes match the destination, the local one is the **most specific**, matching all 32 bits of the IP.

The route's [[Metric and AD|metric and administrative distance]] **do not** have any influence on which route is picked for forwarding a packet. These values are only used to decide which route gets installed on the routing table.