IPv6 has many types. These define how an IPv6 may be used, on which situations, and so on. In a way, this is similar to IPv4, in the sense that IPv4 also has special addresses that are bound to certain uses (take for example the 127.0.0.0/8 network for example, that is used only for loopback interface addresses).

## Global Unicast

Global unicast addresses are globally routable, unique addresses that can be used on the public internet. As such, each global unicast IPv6 address is unique and there can not be two equal addresses of this type. The general structure for this type of address is as follows:

- **A 48 bit global routing prefix**: this generally is assigned by the [[ISP]] and identifies a global public network;
- **An 16 bit subnet ID**: this subnet ID can be used by the client to subnet their network. In conjunction with the routing prefix, this makes for the network prefix.
- **A 64 bit host identifier**: this identifies a unique host inside the network.

**ALL ADDRESSES** that are not used for special cases are valid global unicast IPv6 addresses.

## Unique Local

Unique local IPv6 addresses are similar to IPv4 private addresses: they are not routable on the public internet (ISPs will simply drop packets with IPv6 on this range), and are used only for LAN communication. Addresses in this range must be NATed before going to the public internet.

Unique local IPv6 addresses need to use the address block of `FD00::/8`, so addresses from `FD00::/8` to `FDFF:FFFF:FFFF:FFFF:FFFF:FFFF:FFFF:FFFF/8` are unique local. The structure for this generally is the following:

- **(Required) A 8 bit unique local prefix**: this identifies a unique local address, as defined in RFC 4193. The prefix is [[Number Notation Prefix|0xFD]] or [[Number Notation Prefix|0b11111101]];
- **(Variable) A 40 bit global ID**: this is the network ID. Although, as a "private" IPv6, this does not need to be globally unique, it is a good practice to set this to a random number;
- **(Variable) A 16 bit subnet ID**: this identifies the subnet for the network. In conjunction with the last 56 bits, it makes for the network prefix;
- **(Variable) A 64 bit host identifier**: this identifies a unique host inside the network.

## Link Local

This is kind of a "special" unique local type of address. It is not routable on the public internet nor any network (any router will simply drop packets with link local destinations). Link local addresses are only used for single-link communications (like point-to-point). For example, some common uses for link local addresses are:

- Routing protocol peering: OSPFv3 uses link-local addresses for routing between neighbors;
- Next-hop addresses for static routes;
- NDP (Neighbor Discovery Protocol, the IPv6 ARP's replacement).

Also, link local addresses use EUI-64 to create the host identifier part of the interface address, and is automatically created for each interface that has IPv6 enabled. Since link local interfaces do not belong to any specific network, the rule is to use the network prefix of `FE80::/64`.

## Multicast

Although **IPv6 does not have broadcast addresses like IPv4**, it does contain multicast addresses (one-to-many communication, selective groups). The rule is to use the `FF00::/8` network, changing the address according to the desired destination. Here is a table with the IPv6 multicast addresses:

|         Destination        | Multicast address | IPv4 equivalent |
| -------------------------- |-------------------|-----------------|
| All nodes (like broadcast) | FF02::1           | 224.0.0.1       |
| All routers                | FF02::2           | 224.0.0.2       |
| All OSPF routers           | FF02::5           | 224.0.0.5       |
| All OSPF DRs/BDRs          | FF02::6           | 224.0.0.6       |
| All RIP routers            | FF02::9           | 224.0.0.9       |
| All EIGRP routers          | FF02::A           | 224.0.0.10      |

Also, IPv6 multicast have a feature called scopes. This defines the "distance" a broadcast packet can possibly reach before being dropped. The scopes are:

- Interface-Local: the multicast does not leave the device. The packet reaches all the interfaces within the same node. Network prefix is `FF01::/16`;
- Link-Local: the multicast hits only devices within the same subnet. Network prefix is `FF02::/16`;
- Site-Local (**not on CCNA exam scope**): reaches all the devices in the same site. Must be configured by the network engineer and is forwarded only between routers on the same site. Network prefix is `FF05::/16`;
- Organization-Local (**not on CCNA exam scope**): same as site-local, but can travel through a WAN connection, hitting devices on other sites. Network prefix is `FF08::/16`;
- Global (**not on CCNA exam scope**): can be forwarded on the internet (although it will not hit every single node on the internet). Network prefix is `FF0E::/16`;

Here is an image to illustrate that:
![[Multicast Scopes.png]]

## Anycast

This is a new feature of IPv6.  It is defined as "one-to-one-of-many". Basically, a pool of nodes are configured with the same IPv6 addresses and this interface is set as 'anycast'. Then, when a host sends a packet to this address, the device looks up it's routing table and forward the packet to the nearest router (based on [[Routing Metrics|routing metric]]). Devices with anycast addresses use a routing protocol to advertise these interfaces.

Also,  anycast addresses do not have a specific range (they use regular, global unicast addresses). Here is an example of a router configured with a anycast address:

``` IOS
R1(config-if)#ipv6 address 2001:db8:1:1::99/128 anycast
R1(config-if)#
R1(config-if)#do show ipv6 interface g0/0
GigabitEthernet0/0 is up, line protocol is up
  IPv6 is enabled, link-local address is FE80::EF8:22FF:FE36:8500
  No Virtual link-local address(es):
  Global unicast address(es):
    2001:DB8::EF8:22FF:FE36:8500, subnet is 2001:DB8::/64 [EUI]
    2001:DB8:1:1::99, subnet is 2001:DB8:1:1::99/128 [ANY]
    [...]
```

## Other Types of Addresses

- Unspecified IPv6: denoted as `::`, it is used when the device does not know it's IPv6. Default routes are configured to `::/0`, similar to IPv4's `0.0.0.0`;
- Loopback address: denoted as `::1`, it is the same as IPv4's loopback address range `127.0.0.0/8`, but using just one address;
- Solicited-Node Multicast Address: this type is important for the [[NDP]] (Neighbor Discovery Protocol). It is formed from the interface's global unicast address. The structure of the type is simple: append the last 6 hex digits of the global unicast address to the `FF02::1:FF` prefix. For example, a address of `2001:DB8::EF8:22FF:FE36:8500` would have a solicited-node address of `FF02::1:FF36:8500`.