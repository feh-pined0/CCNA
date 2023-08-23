When configuring IPv6 on Cisco devices, these commands can be helpful:

- `ipv6 address [address/mask] | [net prefix/mask eui-64]` - configures the interface's IPv6 address using the address and mask, or using the EUI-64 method.
Example:

```IOS
R1(config)# int g0/0
R1(config-if)# ipv6 address 2001:db8:0:1::/64 eui-64
R1(config-if)#
R1(config-if)# do show ipv6 int brief
GigabitEthernet0/0 [up/up]
  2001:DB8:0:1:F2A:4FFF:FEA3:B1 [EUI-64]
```

- `show ipv6 neighbor` - shows the IPv6 NDP neighbors discovered on the device's interfaces.
Example:

```IOS
R1# show ipv6 neighbor
IPv6 Address                  Age  Link-layer Addr  State  Interface
FE80::C802:9FF:FE7C:8         0    ca02.097c.0008   REACH  Gi0/0
2001:DB8::78:9ABC             0    ca02.097c.0008   REACH  Gi/0/
```