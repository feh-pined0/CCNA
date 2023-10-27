These commands are useful when trying to configure OSPFv2 on Cisco devices:

- `router ospf [proccess-id]` - enables the OSPF process on the router and sets it's ID, while entering the OSPF configure mode for this process.
```IOS
R1(config)# router ospf 1
R1(config-router)#
```

- `network [network wildcard-prefix] area [area-id]` - sets all the interfaces that match the network on the router to be on the selected area. These interfaces then try to become neighbors with other routers on the same area and exchange LSAs.
```IOS
R1(config-router)# network 10.0.12.0 0.0.0.3 area 0
```

- `passive-interface [interface-id] [default | cr]` - sets the interface to passive mode, preventing it from sending OSPF hello messages. The interface will still send LSAs to OSPF neighbors on that interface. Default makes so that all interfaces have `passive-interface` enabled.
```IOS
R1(config-router)# passive-interface g0/2
```

- `default-information originate` - makes the OSPF process advertise a candidate default route on the area it's on.
```IOS
R1(config-router)# default-information originate
```

- `router-id [RID]` - manually configures the router id of this router. The priority order for RID is: 1. Manually configured; 2. Highest loopback interface IP address; 3. Highest physical interface IP address.
```IOS
R1(config-router)# router-id 1.1.1.1
% OSPF: Reload or use "clear ip ospf process" command, for this to take effect
```

- `distance [AD]` - manually configures the router's OSPF [[Metric and AD|administrative distance]].
```IOS
R1(config-router)# distance 80
```

- `ip ospf [ospf-process] area [area-id]` - manually configures an interface into an OSPF process and area.
```IOS
R1(config-if)# ip ospf 1 area 0
```

- `ip ospf priority [0-255]` - manually configures the interface port priority for the OSPF process.
```IOS
R1(config-if)# ip ospf priority 255
```

- `show ip protocols` - displays information about the routing protocol being used.
```IOS
R1# show ip protocols
*** IP Routing is NSF aware ***

Routing Protocol is "ospf 1"
  Outgoing update filter list for all interfaces is not set
  Incoming update filter list for all interfaces is not set
  Router ID 172.16.1.14
  It is an autonomous system boundary router
Redistributing External Routes from,
  Number of areas in this router is 1. 1 normal 0 stub 0 nssa
  Maximum path: 4
  Routing for Networks:
    10.0.12.0 0.0.0.3 area 0
    10.0.13.0 0.0.0.3 area 0
    172.16.1.0 0.0.0.3 area 0
  Passive Interface(s):
    GigabitEthernet2/0
  Routing Information Sources:
    Gateway          Distance      Last Update
    4.4.4.4               110      00:00:08
    2.2.2.2               110      00:01:07
    3.3.3.3               110      00:01:14
    192.168.4.254         110      00:02:29
  Distance: (default is 110)
```

- `show ip ospf neighbor` - displays information about neighbors.
```IOS
R1# show ip ospf neighbor

Neighbor ID   Pri    State     Dead Time   Address     Interface
3.3.3.3         1    FULL/DR   00:00:39    10.0.13.2   GigabitEth1/0
2.2.2.2         1    FULL/DR   00:00:31    10.0.12.2   GigabitEth0/0
```

- `show ip ospf interface [interface | brief]` - displays information about OSPF enabled interfaces.
```IOS
R1# show ip ospf interface brief

Interface   PID  IP Address      Cost   State     Nbrs F/C
Gi0/0       1    192.168.2.2/29  1      DROTH     2/3
Gi1/0       1    10.0.3.1/24     1      DR        0/0
```

- `ip ospf network [network-type]` - sets the network type for this interface.
```IOS
R1(config-if)# ip ospf network point-to-point
```

