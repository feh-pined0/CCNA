Imagine the following network topology:

![[image-removebg-preview(1).png]]

This is a simple, nice and redundant network topology: it has nice layer 2 redundancy, thanks to [[Classic STP|spanning-tree]] and two internet links: **R1** and **R2**.

But notice one thing: imagine now that R1 goes down, or that cables between SW1 and R1 suddenly broke. Could PC0 and PC1 connect to the internet after that? The answer is no, as common clients can only have **one default gateway**. See, if R1 and R2 were directly connected and R1 went down, R2 probably could figure out another route to the internet through ISP2, maybe through a [[Floating Static Route|floating static route]], maybe through a [[Link State Routing Protocols|dynamic routing protocol]], but end hosts do not have that.

Because of this, **First Hop Redundancy Protocols** are used.

First hop redundancy protocols work by assigning a **VIP** (Virtual [[IPv4 Addressing|IP]]) as the default gateway. Then, two or more [[Routers|routers]] are configured to "share" that IP, one at the time. The **active** router will use that virtual IP as it's interface IP, and forward packets accordingly, while the other routers will be in a **standby** mode, monitoring the active router.

If a active router goes down or becomes unresponsive, the next router takes the virtual IP and begins forwarding the packets itself. 