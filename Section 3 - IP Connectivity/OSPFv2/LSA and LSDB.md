*Link State Advertisements* and *Link State DataBase* are two major components of OSPF.

The link state advertisements are PDUs sent by OSPF routers to advertise about networks connected to them. They contain information such as the route's destination, cost (metric) and RID. OSPF enabled routers will flood these PDUs until all routers on the same network have the same LSDB.

The link state database holds information about all LSAs received on the router. It functions as a kind of map, having information about all the routes advertised by OSPF neighbors.

## Note

LSAs expire and have to be send again in a defined interval in order to stay relevant. The default timer for is 30 minutes.