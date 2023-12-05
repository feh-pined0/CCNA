
When deploying Cisco's solutions for campus and office automation, these three terms are used frequently and they define different aspects and parts of the overall network.

![[Example DNA Center Network Controller.png]]

## Underlay

The *Underlay* of a [[SDN]] is the part of the network that consists of the physical devices and the connections they make. This is basically the network topology as seen from a physical map.

>The underlay of a network:
>![[Network Underlay.png]]

This underlay is a fully routed (usually a [[Spine-Leaf]] architecture) network that provides IP connectivity to other parts of the network, making the use of [[Classic STP|STP]] unnecessary.

In this underlay, some terms are defined for:
- **Edge Nodes**: nodes that connect end hosts to the network (in the case above, the rightmost and leftmost [[Switches|layer 3 switches]] are edge nodes);
- **Border Nodes**: nodes that connect devices to an outside part of the network such as a WAN router or an ISP (for example, in the case above it could be one of the center switches);
- **Control Nodes**: nodes that use LISP to perform various control plane actions;

## Overlay

The *Overlay* of a SDN is the logical network that forms on top of the physical network. In the overlay, network devices such as controllers maintain the control plane of the network, setting up things like routing protocols, device configurations, etc.

A common technology used in the overlay is VXLAN. Because SDNs are usually fully routed networks, there has to be some way to create layer 2 connectivity between network segments. VXLAN does just that by **creating a virtual LAN segment where frames are encapsulated and carried over the layer 3 network**. VXLAN is considered the data plane of SDNs in general.

For example, here is a ethernet frame being transport in the overlay VXLAN by using the physical devices on the underlay. Routing information is provided by LISP running in the overlay network, specifically SW3:

![[Network Overlay.png]]

## Fabric

The *Fabric* of a SDN is simply the converged overlay and underlay together. So, the combination of the physical and logical networks in a SDN forms the fabric.

## Cisco DNA Center on the topology

Cisco DNA Center is one of many SDN controllers. In a automated campus network, the DNA Center appliance would make the intermediate field between the fabric and the network admins. So, for example, configurations about which routing protocol to use on the underlay would be done by a network admin using the DNA Center's APIs, which in turn would configure the fabric to use that routing protocol.

Another example could be that a network admin want to block some traffic from point A to B. He/She would configure it using Intent-Based Networking on a DNA Center appliance, which in turn would configure the overlay network to comply with that policy.

