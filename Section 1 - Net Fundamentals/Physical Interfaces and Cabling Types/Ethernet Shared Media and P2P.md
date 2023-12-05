Ethernet is the main technology that binds networks. It's through ethernet standards and protocols that devices communicate with each other on the network. When it comes to binding the devices physically, there are two ways of doing it: through a shared media, or point-to-point.

Shared media was the first method of binding devices together on a network. It consisted of connecting all the devices on a single cable (usually a coaxial cable with a termination) and use that to transmit and receive ethernet frames (hence the "shared" in the name).

This is not ideal (to say the least). Although it innovated at the time, this model of media could cause many problems. For instance, if any 2 computers were to transmit data at the same time, a collision would occur at the wire, causing the frames to be lost and have to be re-transmitted. Collisions slow down the network a lot, so a workaround was invented: the **CSMA/CD** (*Carrier Sense Multiple Access/Collision Detection*). Devices would "listen" on the wire to check if any traffic was going through before transmitting any data and, if there was, would wait until there wasn't to transmit it. It partially solved the problem.

![[Shared Media Network.png]]

When HUBs started being used, they implemented CSMA/CD, but that too couldn't prevent collisions from happening. So, the necessity to separate devices in smaller collision domains brought the invention of the switch.

A [[Switches|switch]] is a "smart" HUB. For each device connected it creates a separate, layer 2 collision domain by storing the connected device's MAC address in a internal memory. Then, when an ethernet frame is [[Frame Switching|forwarded]] through this switch to this MAC address, it doesn't need to [[Frame Flooding|flood]] the frame to all ports, but rather just forward the frame to that specific port. It essentially separates the entire network (that was one entire collision domain, using a shared media) into various point-to-point connections, each with their own collision domains.

![[Example HUB.png]]

## Brief

Ethernet shared media is a connection that is shared across multiple devices. It has a single collision domain across these devices. All devices connect to the same media.

Point-to-Point connections are isolated connections from one device to another. They can be literal, physical connections (such as a computer to a switch) or logic connections across the layer 2 (such as a computer to computer through a layer 2 switch).