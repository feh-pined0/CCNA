When traffic arrives at a device and needs to be forwarded, it gets placed in a queue to be processed. This is a default structure for handling high amounts of data.

## Queue Handling

In Cisco devices, these queues are handled in a FIFO (First In, First Out) manner by default, meaning that packets that arrived first should be forwarded first, no priority. This can be observed on an interface basis (each interface has it's queue):

![[Pasted image 20231107205753.png]]

## Queue Overflow

When packets are buffered in a queue faster than the interface can output them, **exceeding packets are dropped** until the queue is freed again (this is called a **Tail Drop**). This can cause a problem known as **TCP Global Synchronization**.

When these dropped packets belong to a TCP session, the [[TCP|Transmission Control Protocol]] will acknowledge that the packet did not arrive at destination and will re-transmit it, but it will also lower its **window size** field in order to transmit lower size segments. If all TCP sessions lower the window size at the same time, it will cause a under utilization of the network. Then, all sessions will gradually increase the window size, until the network is congested again, at which point the packets will be dropped.

These TCP sessions will continuously do this in a synchronized manner (thus the name).

#### The Solution

**RED** (Random Early Detection) can be used to prevent TCP Global Synchronization. This mechanism will detect the rapid increase in network congestion and select random TCP flows to drop packets from. This will make so that only those specific selected flows slow down, while others continue normally.

**WRED** (Weighted Random Early Detection) is an improved version of this mechanism, in which the **traffic class** is used as weighting parameter for the selection of the TCP flow to be dropped, allowing for granular configuration of the queuing strategy.

# Queue Management

Different methods can be used to manage a queue in order to prevent overflows and congestion. Generally, an interface will have multiple queues that share the same physical bus. These queues will take turns using the physical bus to send traffic, and these "turns" are managed by a scheduler.

![[Pasted image 20231108173830.png]]

The process for classification determines which traffic ends up in which queue, and then a second algorithm is used to *prioritize* queues when using the physical bus. These can be:

- **CBWFQ** (Class-Based Weighted Fair Queuing): this method consists in cycling through each queue in order, but reserving a percentage of the physical bus' [[Network Resources|bandwidth]] to more important queues, sending more data from the higher priority ones (each queue gets its turn, but higher priority consumes more time and resources of the forwarding device).
![[Pasted image 20231108174454.png]]

- **LLQ** (Low Latency Queuing): this method is more aggressive but it greatly reduces network resources variation, resulting in lower latency and jitter. It consists of assigning a **strict priority queue** from which packets are **always** sent first. Other queues will idle until the strict priority one is empty. This can cause problems if the strict queue is always active, but it can be resolved with **interface bandwidth policing**.
![[Pasted image 20231108174936.png]]

## Bandwidth Policing and Shaping

With these methods, a interface can buffer (shaping) or drop (policing) traffic if it exceeds a configured rate.

![[Pasted image 20231108175349.png]]

