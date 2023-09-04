Cisco switches have five default VLANs pre-configured:

- 1 - this is the default VLAN. All access switchports will be bound to this VLAN.
- 1002 to 1005 - these VLANs were used to bridge ethernet networks with other networks that did not use ethernet (such as token ring and fiber distributed data interface).

Traffic in the default VLAN is usually untagged. This can be changed by setting the native VLAN.

## Native VLAN

The native VLAN indicates to the device which VLAN should have untagged traffic. This means that any traffic that belongs to the native VLAN forwarded **from** a [[Trunk Ports|trunk port]] will **not** be dot1q encapsulated, and any traffic received untagged on a trunk port will be assumed to belong to the configured native VLAN.

> Traffic from native VLAN on trunk port = **untagged**
> Traffic on trunk port untagged = **native VLAN** (generally VLAN 1)