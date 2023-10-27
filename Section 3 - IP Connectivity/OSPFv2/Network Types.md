OSPF has different network types that change how the protocol works in some ways. These types are defined according to the type of connection between the routers on the topology:

- **Broadcast Network**: enabled on connections **Ethernet** and **FDDI**;
- **Point-to-point Network**: enabled on connections **PPP** and **HDLC**;
- **Non-broadcast Network**: enabled on **Frame Relay** and **X.25**;

# Broadcast

The more common type of OSPF network. In this type:

- Routers discover neighbors *dynamically* by sending [[Neighbors|hello messages]] on the multicast address `224.0.0.5`;
- A **Designated Router** and **Backup Designated Router** are elected;
- Any other router becomes a **DROther** router;

#### DR & BDR Election

This election bases off of two parameters:

1. Highest OSPF [[Useful OSPFv2 Commands|interface priority]];
2. Highest Router ID;

When forming neighbor adjacency, all routers exchange their router IDs in the [[Neighbors|2-Way]] step. From this they can calculate the first and second place with these parameters to become the DR and BDR, respectively.

Any router will then form a **FULL adjacency** to the DR and BDR and exchange LSAs, while forming only a **2WAY neighbor** with other DROther routers.

*Routers will only exchange LSAs with the DR and BDR.*
*Messages to the DR and BDR use multicast address `224.0.0.6` instead of `224.0.0.5`*.
*Routers are only considered adjacent when forming a full neighbor relationship.*
#### DR & BDR Topology Changes

Once elected, DR and BDRs **will not** change unless one of them goes down. This means that, even if a port priority is changed, a new router is added or a router ID is changed the DR and BDR will stay the same.

If the DR goes down, the BDR takes it's place and a new election for the BDR is triggered.

# Point-to-Point

In point-to-point OSPF networks, there are some small differences. This type of network is used on serial links using **HDLC** or **PPP** encapsulation by default.

As these encapsulation protocols assume only one point-to-point connection, there is no need to elect a BR and a BDR. Although that is the only major difference.

One thing to keep in mind is that it is possible to manually [[Useful OSPFv2 Commands|change the OSPF network type of an interface]]. This is useful, for example, when configuring an ethernet link that only connects to another router (which is similar to a point-to-point connection).