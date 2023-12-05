
When going through the process of building the switch MAC address table, the device needs to first learn which devices are connected at which ports. It can be done in two major forms:

- **Actively (manual)**: a CAM (*Content Addressable Memory*) table entry can be manually added by the network engineer that is configuring the device;
- **Passively (automatic)**: a CAM table entry is added dynamically each time the switch receives a frame with a unknown source MAC address. This MAC is added to the CAM table along with the receiving interface name and VLAN;

For example, this switch (*SW1*) have an empty CAM table:

![[Example CAM Table.png]]

When generating traffic from *PC0* to *PC2*, it is notable that the switch appends the frame's information to it's MAC address table:

![[Example ARP CAM Table Update 2.png]]

> Note that first line in the frame description: "The frame source MAC address does not exist in the MAC table of Switch. Switch adds a new MAC entry to its table."

The switch then [[Frame Flooding|floods]] the frame to all other ports on the device.

It is important to note too that dynamic CAM table entries expire in 300 seconds or 5 minutes. This can be configured but this is the default behavior.