OSPF route costs are calculated following a similar approach to STP's [[Root Cost Calculation|root cost calculation]]. Physical interfaces are assigned a cost that is added to a route's metric each time it's [[LSA and LSDB|LSA]] is shared among the routers in the area.

The main difference is that OSPF does not have a pre-defined value for each interface bandwidth, but uses a formula to calculate this "on-the-go". It is as follows:

> $M = ceil(\frac{B}{100})$
> 
> Where:
>   M is the metric
>   B is the interface bandwidth
>   100 is a pre-defined **reference bandwidth**

Because of this formula, interfaces with bandwidths greater then 100 mbps all get rounded to 1 cost, though this could be changed in the OSPF configuration.

