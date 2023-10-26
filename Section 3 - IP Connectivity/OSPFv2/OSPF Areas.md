As OSPF is a link state protocol, it needs more resources from the router running it. Because of this, having a single, monolithic networking running a single "instance" of OSPF can be very heavy on the routers. To solve such case, OSPF can divide a single network in multiple *areas*.

OSPF areas are smaller groups of routers that share the same [[LSA and LSDB|LSDB]]. Routers from different areas have different LSDBs. Each area of the OSPF topology **needs** to be connected by at least one router to the area 0 (also called the **Backbone area**).

Routers are labeled according to their position on the topology:

- **Internal Router** (IR): is a router that has all of it's interfaces inside one area;
- **Area Border Router** (ABR): is a router that connects two areas (have interfaces in mode than one area);
	- These routers contain two LSDBs: one for each area it is into.
- **Backbone Router** (BR): any router that has an interface on the backbone area (area 0). This includes ABRs.
	- This means that a router can be an ABR and a Backbone router at the same time.
- **Autonomous System Boundary Router** (ASBR): it is a router that connects to an external network (such as the internet) and originates information about it using the `default-information originate` command.

## Area Defining Rules

There are some rules when defining OSPF areas:

- OSPF areas should be *contiguous*. This means that the same area must not be divided into multiple segments, but should be coupled together.
>This is an example of a non-contiguous OSPF area 1:
>![[Pasted image 20231024162957.png]]
>In this case, the "second" area 1 should be another area entirely.

- All areas **must have** at least one ABR connected to the backbone area (area 0);
- OSPF interfaces on the same subnet **must be** on the same area;
