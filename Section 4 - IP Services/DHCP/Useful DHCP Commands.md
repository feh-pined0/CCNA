These commands can be useful when trying to configure IP parameters on Cisco devices:

- `ip dhcp excluded-address <ip-addr> [final-ip-addr]` - defines an address (or a set of addresses) to exclude from the DHCP lease process. These addresses will not be handed to clients over DHCP.
```IOS
R1(config)# ip dhcp excluded-address 192.168.1.1 192.168.1.10
```

- `ip dhcp pool <pool-name>` - creates and enter the configuration mode for a DHCP pool.
```IOS
R1(config)# ip dhcp pool vlan10
R1(dhcp-config)#
```

- `network <net-prefix> <[CIDR netmask | netmask]>` - defines a network to lease IPs to.
```IOS
R1(dhcp-config)# network 192.168.10.0 255.255.255.0
```

- `network <net-prefix> <[CIDR netmask | netmask]>` - defines a network to lease IPs to.
```IOS
R1(dhcp-config)# network 192.168.10.0 255.255.255.0
```

- `dns-server <DNS-server-IP>` - includes the specified DNS server into the `option 6` of the DHCP offer. Can be administered more than once to include more servers in the response.
```IOS
R1(dhcp-config)# dns-server 8.8.8.8
R1(dhcp-config)# dns-server 8.8.0.0
```

- `domain-name <domain-name>` - defines the domain name for this DHCP pool.
```IOS
R1(dhcp-config)# domain-name atiweb.intranet
```

- `default-router <router-ip>` - defines the default gateway for the DHCP leases (`option 3`).
```IOS
R1(dhcp-config)# default-router 192.168.10.1
```

- `lease <days> <hours> <minutes> | infinite` - configures the lease expiration time.
```IOS
R1(dhcp-config)# lease 0 5 30
```

- `ip helper-address <dhcp-server>` - defines a server for the DHCP relay agent to forward DHCP broadcasts to. Should be administered from an interface scope.
```IOS
R1(config-if)# ip helper-address 192.168.10.10
```

- `ip address dhcp` - configures the interface's IP address to be configured using DHCP.
```IOS
R1(config-if)# ip address dhcp
```

- `show ip dhcp binding` - displays information about this device's DHCP server leases and bindings.
```IOS
R1# show ip dhcp binding
Bindings from all pools not associated with VRF:
IP address      Client-ID\              Lease expiration       Type
                Hardware address\
                User name
192.168.1.11    0100.0c29.e727.39       Jan 24 2021 10:52 AM   Automatic
```

