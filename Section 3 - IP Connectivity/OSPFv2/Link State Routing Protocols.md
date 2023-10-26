Dynamic routing protocols can use various methods to determine a path to a destination, and which path is the best. Based on these choices, routing protocols can be categorized in 3 types:

- **Distance Vector**: usually, distance vector routing protocols use hop-count as their metrics;
- **Link State**: protocols of this type use the state of the interfaces as their method to operate, such as interface state (up or down), speed and duplex mode;
- **Path Vector**: ?

OSPF is a link state type protocol. When using OSPF, routers will advertise information about their interfaces, which networks they connect to, the metric, speed and duplex mode of the exit-interfaces, etc.

From this, [[Routers|routers]] will be able to exchange information and form a map of the active network, being able to then calculate the best paths for each destination. Usually, this type of protocol uses more resources, but are faster when responding to changes in the topology.