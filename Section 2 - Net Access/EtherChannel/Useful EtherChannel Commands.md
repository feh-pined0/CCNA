- `show etherchannel summary` - displays a summary with etherchannel information, such as link status, groups, etc:
![[Show Etherchannel Summary.png]]

- `show etherchannel port-channel` - displays information about the ports bundled on an etherchannel group. It is useful to check which protocol mode the port-channel is using:
![[Show Etherchannel Port-Channel Example.png]]

- `port-channel load-balance [mode]` - defines which load-balancing strategy should be used when forwarding EtherChannel frames through physical links:
```IOS
ASW1(config)# port-channel load-balance ?
  dst-ip Dst      IP Addr
  dst-mac Dst     Mac Addr
  src-dst-ip      Src XOR Dst IP Addr
  src-dst-mac     Src XOR Dst Mac Addr
  src-ip          Src IP Addr
  src-mac         Src Mac Addr
```

- `show etherchannel load-balance` - displays information about load-balancing strategy being used:
```IOS
ASW1# show etherchannel load-balance
EtherChannel Load-Balancing Configuration:
        src-dst-ip

EtherChannel Load-Balancing Addresses Used Per-Protocol:
Non-IP: Source XOR Destination MAC address
  IPv4: Source XOR Destination IP address
  IPv6: Source XOR Destination IP address
```