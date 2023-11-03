As with many IP protocols, DHCP has a problem regarding it's **necessity to use broadcast addresses to discover a server**. This is because servers do not necessarily need to be in the same subnet as clients do, but **broadcast messages do not leave the subnet they are cast into**. This causes clients to not be able to reach the centralized DHCP server and thus do not get DHCP leases.

For this, DHCP Relay Agents can be configured on the subnet's gateway to unicast the DHCP client requests directly to the DHCP server. This works by:

- Overwriting the **DHCP outgoing client request's source IP address** from `0.0.0.0` to the gateway's IP address, and the **request's destination IP address** from `255.255.255.255` to the unicast address of the DHCP server's address;
- Overwriting the **server response's source IP address** to the gateway's IP address and the destination to either `255.255.255.255` (if the client's bootp flags were set to broadcast the response) or the unicast address of the client;

The configuration can be done quite easily:

```IOS
R1(config-if)# ip helper-address x.x.x.x
```

> Where `x.x.x.x` is the DHCP server's IP address.

