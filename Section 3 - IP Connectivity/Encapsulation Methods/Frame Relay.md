*Frame Relay* is a layer 2 (*data-link*) encapsulation and packet-switching protocol that was replaced by Ethernet.

It encapsulates a layer 3 packet with header and a trailer data in order for physical (layer 1) transport to happen. **Frame Relay only works with serial media**.

Frame Relay works by creating virtual circuits that connect multiple routers with a frame relay switch. This switch manages these virtual circuits and their routes:

![[Pasted image 20231204184502.png]]

The frame relay switches do this by **creating a map between a layer 3 protocol address** (usually [[IPv4 Addressing|IP]]) and a **DLCI** (*Data Link Connection Identifier*). When a packet using the defined layer 3 protocol, with a matching address enters the device, the border router uses that mapping to send the packet through the appropriate DLCI.

When this frame arrives at central frame relay switch, it gets forwarded using one of the virtual circuits to the destination.

>Example of a Frame Relay frame:
>![[Pasted image 20231204185420.png]]

## Configure Frame Relay on Border Routers

\*<span style="color:#ff0000">This is not required by the CCNA</span>

To configure frame relay on border routers:

1. Connect the devices using either side of the serial cable (DTE or DCE);
	1. If DCE side is connected, configure the clock rate on the interface;
2. On the interface, configure a frame relay encapsulation method by administering the `encapsulation frame-relay` command;
3. Again on the interface, set it's IP address and the interface DLCI with the `ip address` and `frame-relay interface-dlci <dlci>` commands;

Example configuration:
```IOS
interface Serial0/0
  no ip address
  encapsulation frame-relay
!
interface Serial0/0.1 point-to-point
  ip address 20.1.1.2 255.255.255.252
  frame-relay interface-dlci 201
!
interface Serial0/0.3 point-to-point
  ip address 20.1.1.13 255.255.255.252
  frame-relay interface-dlci 203
```