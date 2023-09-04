STP has additional features that enable a network engineer to customize the way STP operates in a topology. There are many features, but for the CCNA exam, only two are necessary:

- **PortFast**: This feature enables a port to go directly to the [[Port States|forwarding state]] upon initialization. This speeds up the process of a access port to begin forwarding frames, as it does not go through the listening and learning stages;
	- PortFast only works on access switchports (not trunk ports);
	- It should **never** be enabled on uplink interfaces that connect to other switches, as it could cause loops in the network.
	- For enabling it:
		- **Globally**: `spanning-tree portfast default`;
		- **Per-Interface**: `spanning-tree portfast`;
- **BPDU Guard**: This protects a port from loops by disabling it upon receiving a BPDU. This can ensure that a PortFast enabled interface does not accidentally connect to another switch, causing a loop.
	- For enabling it:
		- **Globally**: `spanning-tree portfast bpduguard default`;
		- **Per-Interface**: `spanning-tree bpduguard enable`;

Also, it is important to know how to configure which switch will be the [[Classic STP|Root Bridge]]:

- `spanning-tree vlan [VID] root [primary|secondary]` - configures this switch to be the root bridge or the secondary root bridge for this topology. In reality, it sets the switch Bridge ID priority to whatever the current root bridge is, minus 4096.
```IOS
SW1(config)# spanning-tree vlan 1 root primary
SW1(config)# do show spanning-tree
VLAN0001
  Spanning tree enabled protocol ieee
  Root ID    Priority    24577
             Address     cccc.cccc.cccc
             This bridge is the root
             Hello time is 2 sec  Max Age 20 sec  Forward Delay 15 sec
  
  Bridge ID  Priority    24577 (priority 24576 sys-id-ext 1)
             Address     cccc.cccc.cccc
             This bridge is the root
             Hello time is 2 sec  Max Age 20 sec  Forward Delay 15 sec

SW1(config)# do show running-config | include spanning-tree
spanning-tree mode pvst+
spanning-tree extend system-id
spanning-tree vlan 1 priority 24577
```