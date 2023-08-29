An *Access Port* on a [[Switches|switch]] is a interface that is bound to only one LAN or VLAN. This means that any broadcast or link-local multicast traffic received on that port will only be forwarded to other devices on the same LAN or VLAN.

A switch with a default configuration will generally have all ports set to access mode and be configured to VLAN 1, which is a default VLAN created by default (this is also called a *untagged* port).

The `switchport` command is used to configure the ports on the device:

- `switchport mode [access|trunk]` - configures a port to be an access or trunk port;
- `switchport access vlan [VLAN]` - configures the access port to tag frames with this `VLAN`.

An access port can be untagged (set to VLAN 1) or tagged (set to another VLAN other than the default). Also, access ports can have a VLAN set for data traffic, and another VLAN for voice traffic, using the command `switchport voice vlan [VLAN|"untagged"]`.