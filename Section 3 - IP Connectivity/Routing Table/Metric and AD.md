The metric and *administrative distance* are values that a router uses to decide which routes from which protocols actually get placed in it's [[Routing Table|routing table]].

When using dynamic routing protocols, router can receive multiple routes to the same destination. This can be from different routing protocols (such as a router running both [[OSPF]] and [[EIGRP]]) or simply from the same routing protocol on different interfaces.

## Metric

All these dynamic routing protocols use the **metric** value to determine which path is the best. The lower the metric value, the better the path.

However, different protocols have different ways for calculating metric. [[RIP]] for example, uses hop-count to evaluate the metric, so a path that takes 4 hops to reach the destination has a metric value of 4. On the other hand, OSPF defines a hop-cost for each type of interface, based on their speed (similar to [[Root Cost Calculation|802.1D root cost calculation]]), so these costs are summed and the final value is assigned to the route metric.

Because of this, metrics from two different protocols cannot be compared, and another value needs to be used to compare routes.

## Administrative Distance

The *AD* is a pre-defined value that gets assigned to a route based on the **source routing protocol that defined that route**. This is based on which protocol is more modern and reliable:

>![[Pasted image 20230918215241.png]]

Using the example from before, the OSPF route would be included in the routing table, and the RIP route would be discarded, because OSPF's AD is lower than RIP's AD.

# Something to Keep in Mind

Although administrative distance is used to compare routes from different protocols, it **is not used on forwarding decisions**. AD and metric are values used for the router to **decide which routes enter the routing table**, and thus **the routing table will not have multiple routes to the same destination**, although it can have backup routes configured (see [[floating static routes]]).