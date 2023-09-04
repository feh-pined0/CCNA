As [[EtherChannel]] has multiple physical links, traffic can be distributed between them, creating a load-balance.

The general algorithm strategy is as follows:

- A session is formed ([[TCP]]) between any two devices;
- EtherChannel takes note of that, and runs an algorithm to determine which physical link will be used for the connection (generally the less busy link);
- Any frames sent with that session will be forwarded using the same physical link;

This ensures that frames do not arrive [[Out-Of-Order Traffic|out-of-order]].

This load-balancing algorithm can be configured to a certain degree. Source and destination addresses (layer 2 MAC and layer 3 [[IPv4 Addressing|IP]]) can be configured to always use a specific physical link.

EtherChannel load-balancing configuration can be viewed by issuing the `show etherchannel load-balance` command:

```IOS
ASW1# show etherchannel load-balance
EtherChannel Load-Balancing Configuration:
        src-dst-ip

EtherChannel Load-Balancing Addresses Used Per-Protocol:
Non-IP: Source XOR Destination MAC address
  IPv4: Source XOR Destination IP address
  IPv6: Source XOR Destination IP address
```

This configuration can be changed using the `port-channel load-balance [method]` command. Note the "port-channel" instead of "etherchannel". Although the command is not the same, the configuration is.