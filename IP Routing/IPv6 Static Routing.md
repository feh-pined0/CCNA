IPv6 static routes are very similar to IPv4 routes. There are 3 types of static routes (for both IPv6 and IPv4), and they differ on the level of information provided for the routing table:

- **Directly attached**: when defining the static route, the next-hop is defined using only the exit interface of the device. Example: `ipv6 route 2001:db8:0:3::/64 g0/0`. Read as "route traffic to `2001:db8:0:3::/64` network through interface GigabitEthernet0/0". **Note**: this type of route does **not** work with ethernet interfaces, so this command, although accepted by the device, won't produce a usable route and will not work;
- **Recursive**: when defining the static route, the next-hop is defined using only the next device's IP address. Example: `ipv6 route 2001:db8:0:3::/64 2001:db8:0:12::2`;
- **Fully specified**: when defining the static route, the next-hop is defined as both a exit interface and a next-hop address, preventing the router from doing recursive route table look ups. Example: `ipv6 route 2001:db8:0:3::/64 g0/0 2001:db8:0:12::2`;

Also, like IPv4 routing, there are x route scopes for IPv6 static routes, and they differ based on the destination type:

- **Network route**: defines a route to an entire network/subnet. Example: `ipv6 route 2001:db8:0:3::/64 2001:db8:0:12::2`;
- **Host route**: defines a route to a specific host on a network. Example: `ipv6 route 2001:db8:0:3::100/128 2001:db8:0:23::1`. Note the `/128` mask, implying that the whole 128 bits of the address belong to the network mask;
- **Default route**: defines a route to use when no other route in the routing table matches a packet's destination address. Example: `ipv6 route ::/0 2001:db8:0:23::1`;
- **Floating static route**: defines a secondary route to a destination. Also called a backup route, this floating static route's ad (administrative distance) needs to be set up higher than an already configured route on the device. Example: `ipv6 route 2001:db8:0:3::/64 2001:db8:0:23::1 110`. This sets a route to `2001:db8:0:3::/64` network with an AD of 110 (higher AD than a [[OSPF]] learned route).