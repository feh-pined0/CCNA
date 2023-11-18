*ARP Inspection* is a lot like [[DHCP Snooping]]. It inspects ARP requests that arrive on untrusted ports and either drop or forward them based on configured parameters.

The parameters for inspection in ARP are `Source IP`, `Source MAC`, `Target IP` and `Target MAC`. Switches will apply the following default rules:

- If an ARP message is received on a **trusted port**, **the switch forwards it without further inspection**;
- If an ARP message is received on a untrusted port, the switch compares the `Source IP Address` and `Source MAC Address` of the message (not the frame) to the DHCP Snooping Binding Table;
	- If an entry is found for the source MAC and IP and both match, the ARP is forwarded as normal;

To configure ARP inspection, it is also similar to DHCP Snooping:

1. Enable the process for a VLAN:
```IOS
SW1(config)# ip arp inspection vlan 1
```

2. Then, define which ports should be trusted. NOTE: ARP inspection best practices state that any interface that connects to other networking devices should be trusted, as opposed to DHCP snooping, where only uplink ports should be trusted:
```IOS
SW1(config)# interface range FastEthernet0/0-1
SW1(config-if-range)# ip arp inspection trust
```

3. Additionally, rate limits can be configured manually, although they are **configured on untrusted ports by default**, with a default rate of 15 ARP messages per second:
```IOS
SW1(config)# interface range FastEthernet0/0-1
SW1(config-if-range)# ip arp inspection limit rate <message-num> [burst interval <seconds>]
```

## ARP Inspection Without DHCP

Additionally, if DHCP is not being used and ARP inspection is enabled, the switch will drop all ARP messages because it will not have a DHCP snooping binding table to lookup IP and MAC relations. For this case, a **ARP ACL** can be configured to statically permit ARP messages from hosts that match the ACL's MAC and IP addresses:

ARP ACLs are configured a bit different from normal ACLs, as they have to include a MAC address, alongside with the IP address to permit or deny:

```IOS
SW1(config)# arp access-list ARP-ACL-VLAN1
SW1(config-arp-nacl)# permit ip host 192.168.1.100 mac host 0c29.2f1e.7700
SW1(config-arp-nacl)# exit
SW1(config)# ip arp inspection filter ARP-ACL-VLAN1 vlan1
```

