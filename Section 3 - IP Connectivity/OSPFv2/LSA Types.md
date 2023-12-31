There are 11 LSA types, but for the CCNA, only 3 are relevant:

- **Type 1 (Router LSA)**: generated by any OSPF enabled router, it identifies the router by it's router ID. Also, it lists the networks attached to the router's OSPF-activated interfaces;
- **Type 2 (Network LSA)**: generated by the DR of each *multi-access* network (like a [[Network Types|broadcast network type]]). It lists the routers which are attached to the multi-access network;
- **Type 5 (AS-External LSA)**: generated by a ASBR to describe routes to destinations outside the autonomous system (OSPF domain). Basically, an LSA to advertise default routes.

