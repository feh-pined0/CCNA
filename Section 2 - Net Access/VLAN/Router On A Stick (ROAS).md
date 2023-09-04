
When forwarding packets between VLANs (also called *inter-vlan routing*) a layer 3 device is necessary (often a [[Routers|router]] or [[Switches|multi-layer switch]]). Then, for any number of VLANs, an equal number of interfaces are needed: one for each network (the router needs to be in each VLAN network in order to be the default gateway for them).

Router generally do not have a lot of physical interfaces, so using one port for each VLAN is expensive. For this, the ROAS architecture was created.

This architecture use a feature called **sub-interface**, in which is possible to divide a physical interface into multiple, logical interfaces, one in each VLAN.

The step-by-step for configuring Router On A Stick is (in this example, interface `Gi0/1` is used):

1. Enable the interface:
    ```IOS
	R1(config-if)# no shutdown
	%LINK-3-UPDOWN: Interface GigabitEthernet0/1, changed state to up
	%LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/1, changed state do up
    ```
2. Enter sub-interface configuration mode (in this case, `int Gi0/1.10`):
    ```IOS
    R1(config-if)# interface gi0/1.10
    R1(config-subif)#
    ```
3. Set the encapsulation mode to "dot1q", configure the [[802.1Q Header|VID]] and set the [[IP Parameters|IP address]] of the sub-interface:
    ```IOS
	R1(config-subif)# encapsulation dot1q 10
	R1(config-subif)# ip address 192.168.1.62 255.255.255.192
	R1(config-subif)#
    ```

Remember that, while it is good practice to match the VID with the sub-interface's number (like sub-interface `Gi0/1.10` and VID 10), **it is not mandatory**.