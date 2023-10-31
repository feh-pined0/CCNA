These commands are useful when trying to configure HSRP on Cisco devices:

- `standby [group-number] ip [VIP]` - enables HSRP on the interface and configures an VIP.
```IOS
R1(config-if)# standby 1 ip 172.16.0.254
```

- `standby [group-number] priority <0-255>` - manually configures the HSRP router priority. Higher is preferable. In the case of a draw, higher physical IP address wins. Default is `100`;
```IOS
R1(config-if)# standby 1 priority 200
```

- `standby [group-number] preempt` - configures the router to take back the role of "active router" even if another router has already taken that role. The router needs to be eligible to become the active router (higher priority or IP address);
```IOS
R1(config-if)# standby 1 preempt
```

- `standby version [1|2]` - manually configures the HSRP version. Needs to match between routers;
```IOS
R1(config-if)# standby version 2
```

- `show standby` - displays information about the HSRP operation on the router;
```IOS
R1# show standby

GigabitEthernet0/0 - Group 1 (version 2)
  State is Active
    2 state changes, last state change 00:16:30
  Virtual IP address is 172.16.0.254
  Active virtual MAC address is 0000.0c9f.f001
    Local virtual MAC address is 0000.0c9f.f001 (v2 default)
  Hello time 3 sec, hold time 10 sec
    Next hello sent in 1.536 secs
  Preemption enabled
  Active router is local
  Standby router is 172.16.0.252, priority 50 (expires in 9.280)
  Priority 200 (configured 200)
  Group name is "hsrp-Gi0/0-1" (default)
```

