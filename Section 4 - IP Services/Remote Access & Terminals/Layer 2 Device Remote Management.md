Layer 2 devices such as switches do not have layer 3 capabilities such as IP routing. However, they are able to act as a client on networks to provide remote management. This can be done through an **SVI** (Switch Virtual Interface).

To configure a switch for remote access:

1. Define a SVI and configure an IP address and default gateway for it (same as when manually configuring a wired station).
```IOS
SW1(config)# interface vlan10
SW1(config-if)# ip address 192.168.1.253 255.255.255.0
SW1(config-if)# no shutdown
SW1(config-if)# exit
SW1(config)# ip default-gateway 192.168.1.1
```

2. Next, 