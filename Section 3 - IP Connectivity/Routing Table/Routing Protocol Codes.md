When visualizing a routing table, routes are tagged with a routing protocol code. These generally consist of a single letter that identify the protocol used when creating that route.

Some routes do not specifically use any of the dynamic routing protocols, but rather are created following some default behavior (such as local routes).

Here is a print of the routing codes (from a Cisco device running IOS), along with an explanation of each:

```IOS
R1# show ip route

Codes: L - local, C - connected, S - static, R - RIP, M - mobile, B - BGP
D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area
N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
E1 - OSPF external type 1, E2 - OSPF external type 2, E - EGP
i - IS-IS, L1 - IS-IS level-1, L2 - IS-IS level-2, ia - IS-IS interarea
* - candidate default, U - per-user static route, o - ODR
P - periodic downloaded static route
```

- **Local (L)**: (*CCNA relevant*) the "local" route is a route pointing to a /32 (IPv4) or /128 (IPv6) IP address configured on any of the router's interfaces. This means that any local route simply points to the device itself. **This is created automatically on adding an IP address to any interface and enabling it**;
- **Connected (C)**: (*CCNA relevant*) a connected route is a route that is created automatically when adding an IP address to an interface and enabling it. It defines a route to the network that an interface on the router is part of;
	- For example, when configuring an interface with the IP address of `10.10.10.1/24`, a connected route to the `10.10.10.0/24` network is created, because it assumes this network is reachable through this interface.
- **Static (S)**: (*CCNA relevant*) a manually configured route. This type of route is added manually to the routing table and is not formed by any routing protocol (such as RIP and OSPF). By default, **these routes have a metric of 1**, but this can be adjusted.
	- The command for creating a static route is `ip route network netmask [next-hop|exit-interface|exit-interface next-hop]`.
- **Candidate Default (\*)**: (*CCNA relevant*) defines a default gateway/route that matches any IP address, if a more specific route is not found in the routing table.
	- It is defined using the `ip route 0.0.0.0 0.0.0.0 [next-hop|exit-interface|exit-interface next-hop]` command. The `0.0.0.0/0` network matches any IP address and is the least specific network that exists.
