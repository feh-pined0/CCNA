*Virtual Routing and Forwarding* is a virtualization technique that enables layer 3 capable devices to create more than one, global routing table, thus basically creating a separate, virtual router.

This can be used to provide traffic isolation from multiple networks. It operates like a switch with multiple VLANs, but instead of splitting the network into multiple broadcast domains (layer 2) it splits the router into multiple routing tables.

![[Pasted image 20230822205139.png]]

Note that, because the router was split into multiple virtual devices, it is totally possible to assign the same addresses to different interfaces, as long as they reside in a different VRF within the router.

Some useful commands for configuring VRFs:

- `ip vrf [VRF_NAME]` - creates a new VRF instance on the router.
	- Example:

```IOS
R1(config-if)# ip vrf vRouter01
R1(config-vrf)#
R1(config-vrf)# do show ip vrf
  Name             Default RD         Interfaces
  vRouter01        <not set>          
```

- `ip vrf forwarding [VRF_NAME]` - assigns an interface to the chosen VRF_NAME. Note that when administering this command, the assigned interface loses it's IP configuration, due to joining a new virtual router.
	- Example:

```IOS
R1(config)# interface g0/0
R1(config-if)# ip vrf forwarding vRouter01
% Interface GigabitEthernet0/0 IPv4 disabled and address(es) removed due to enabling VRF vRouter01
R1(config-if)# do show ip vrf
  Name             Default RD         Interfaces
  vRouter01        <not set>          Gi0/0
```

- `show ip route vrf [VRF_NAME]` - displays the routing table for the required VRF_NAME instance.