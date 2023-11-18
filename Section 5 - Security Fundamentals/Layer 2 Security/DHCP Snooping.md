*DHCP Snooping* is a security feature of layer 2 devices that prevents common DHCP attacks such as [[DHCP Poisoning|DHCP poisoning]] or [[Spoofing|DHCP starvation]] by configuring a set of trusted and untrusted switchports on which to inspect DHCP messages and drop or forward it depending on a set of rules.

With DHCP snooping, switchport are given a status:

- **Untrusted**: ports that are not trusted and are prone to attacks. These are usually downlink ports, connecting end hosts;
- **Trusted**: ports that are trusted and should be allowed DHCP traffic freely. These are usually uplink ports connecting to gateways and servers;

From this, messages are inspected and dropped according to specific rules:

- If any DHCP message is received on a trusted port, it is forwarded like normal;
- If a [[DHCP Message Types|DHCP server message]] is received on a untrusted port, **it is dropped without inspection**;
- If a DHCP client message is received on a untrusted port, the following inspections are done:
	- For **DISCOVER/REQUEST** messages, if the source MAC address (ethernet frame) does not match the `CHADDR` (layer 7 DHCP message), **the frame is dropped without further inspection**.
	- For **RELEASE/DECLINE** messages, the source IP address (layer 3 internet) is checked against the interface entry in the DHCP Snooping Binding Table. If it does not match, **the message is dropped without further inspection**;

## Configure DHCP Snooping

To enable DHCP Snooping:

1. Enable the global process, then enable the process for individual VLANs:
```IOS
SW1(config)# ip dhcp snooping
SW1(config)# ip dhcp snooping vlan 1
```

2. Configure individual ports as trusted (all are untrusted by default):
```IOS
SW1(config)# interface FastEthernet0/1
SW1(config-if)# ip dhcp snooping trust
```

3. There is also a configuration for DHCP rate limit, to limit the rate of DHCP messages on the interfaces:
```IOS
SW1(config)# interface FastEthernet0/1
SW1(config-if)# ip dhcp snooping limit rate <seconds>
```
>If the threshold is surpassed the interface will be err-disabled. It can be re-enabled manually, or automatically with the `errdisable recovery cause` command.

4. Finally, all this information can be verified with the `show ip dhcp snooping binding`. This will display the DHCP snooping binding table;
## Cisco's Snooping Information Problem

By default, when the DHCP snooping process inspects a DHCP message (on Cisco Switches), a option 82 (information option) is added to the message. This option is usually added by relay agents to add information about the device who forwarded the message.

This option can cause a lot of problems because DHCP snooping **also drop DHCP messages on untrusted ports that have this option**. Because of this, it is often best to disable it:

```IOS
SW1(config)# no ip dhcp snooping information option
```

