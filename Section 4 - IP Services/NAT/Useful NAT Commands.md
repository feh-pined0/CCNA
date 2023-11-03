These commands are useful when trying to configure NAT on Cisco devices:

- `ip nat [inside|outside]` - configures the interface to be labeled as an inside or outside interface, connected to an inside or outside network, respectively.
```IOS
R1(config-if)# ip nat inside
```

- `ip nat inside source static <inside-local-ip> <inside-global-ip>` - configures a **static** translation of the **source** IP address for packets from the **inside** network, from the **inside global address** to the **outside global address**.
	- Can be read as: "always translate this source IP address from the inside network to this inside global IP";
```IOS
R1(config)# ip nat inside source static 192.168.0.143 203.0.54.1
```

- `ip nat inside source list <access-list> [pool <pool-name> | interface <interface>] [overload]` - defines a dynamic translation rule, which translates packets to either one IP from the defined IP NAT pool or the IP of an interface.
	- Can be read as: "translate the IPs in this access-list to any IP of this pool" or "translate the IPs in this access-list to the IP of this interface";
	- The `overload` keyword causes the rule to translate the IPs even if the pool is exhausted, in which case it will append a auto-generated [[Address Overload|layer 4 port number to track the flow]];
```IOS
R1(config)# ip nat pool default-pool 100.0.0.1 100.0.0.5 netmask 255.255.255.0
R1(config)# access-list 1 permit 192.168.0.0 0.0.0.255
R1(config)# ip nat inside source list 1 pool default-pool overload
```

- `show ip nat translations` - displays information about NAT translations on the device (static and dynamic).
```IOS
R1# show ip nat translations

Pro  Inside Global     Inside Local          Outside Local    Outside Global
---  100.0.0.1         192.168.0.167         ---              ---
---  100.0.0.2         192.168.0.168         ---              ---
```

- `show ip nat statistics` - displays information about NAT statistics on the device (translations, interfaces, hits, etc).
```IOS
R1# show ip nat statistics

Total active translations: 2 (2 static, 0 dynamic; 0 extended)
Peak translations: 4, occurred 02:29:00 ago
Outside interfaces:
  GigabitEthernet0/0
Inside interfaces:
  GigabitEthernet0/1
Hits: 34, Misses: 0
CEF Translated packets: 30, CEF Punted packets: 4
Expired translations: 4
Dynamic mappings:

Total doors: 0
Appl doors: 0
Normal doors: 0
Queued Packets: 0
```

