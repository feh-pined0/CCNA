When configuring IPv4 on Cisco devices, these commands can be helpful:

- `show ip interface [interface | "brief"]` - displays information about an IP interface, or a brief of all IP interfaces on the device
Example:

```IOS
R1> show ip int brief

Interface          IP-Address      OK?  Method  Status  Protocol
FastEthernet0/0    192.168.254.254 YES  NVRAM   up      up
FastEthernet0/1/0  unassigned      YES  unset   down    down
Serial0/0/0        172.16.0.254    YES  unset   up      down
```

- `ip address [ipv4 addr [CIDR netmask]] [subnet mask] | dhcp` - sets the IP address and method of the interface. If an address and mask comes after the `ip address` command, the address is configured. If `dhcp` is inputted instead, the interface gets an IP leased from the DHCP server on the network.
Example:

```IOS
R1(config)# interface GigabitEthernet0/0
R1(config-if)# ip addr 10.60.162.127 255.255.255.0 -> same thing
R1(config-if)# ip addr 10.60.162.127/24            -> same thing
R1(config-if)# do show ip interface g0/0

Interface           IP-Address      OK?  Method  Status  Protocol
GigabitEthernet0/0  10.60.162.107   YES  manual  up      up
```

- `ip default-gateway [gateway_address]` - sets the interface's default gateway router. Useful for configuring static IP interfaces.
Example:

```IOS
R1(config)# interface GigabitEthernet0/0
R1(config-if)# ip default-gateway 10.60.162.1
```

