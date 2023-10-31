*Virtual Router Redundancy Protocol* is an open standard [[First Hop Redundancy Protocols|FHRP]].

In VRRP:

- A **master** and **backup** router are elected.
- Routers communicate with each other using the multicast address `224.0.0.18`;
- Routers advertise a virtual MAC address for this VIP of `0000.5e00.01xx`, where `xx` is the VRRP group;

Each router can be the master per subnet, making it possible to load-balance between different subnets.