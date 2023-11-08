As [[QoS]] is a means to prioritize traffic on the network, some parameters need to be analyzed and compared to comprehend which type of packets should navigate unconditionally and which should wait or even be dropped.

For this analysis, four parameters are relevant:

- **Bandwidth**: measured in bits per seconds (or it's multiples of 1000 such as Kpbs, Mbps, etc), the bandwidth is the link's overall capacity. For example, a `GigabitEthernet` interface should have a bandwidth of $1000000000 bps$.
>Here is an example of an output for a gigabit interface on a Cisco router:
>![[Pasted image 20231107202807.png]]
>Bandwidth is not always determined by the interface's parameters. There are such cases when a hardware limitation (such as the router's CPU power for example) can cap the bandwidth, even if the interface is capable of pushing it.

- **Delay**: this is the amount of time it takes for a packet to reach the destination. This can be divided into **one-way delay** (time from source to destination) and **two-way delay** (from source to destination and back with the reply. Sometimes called latency).
- **Jitter**: the variation in one-way delay between packets from the same application.
	- For example, a connection has high jitter if some packets take 20 ms to reach destination and others take 90 ms;
- **Loss**: the percentage of packets that do not reach destination, by either being dropped by devices or occurrence of any errors in general.