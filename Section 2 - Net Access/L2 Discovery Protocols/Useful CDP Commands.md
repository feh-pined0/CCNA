- `show cdp` - displays information about CDP timers, and informs if CDP is enabled/disabled;
    ```
    R1#show cdp
    Global CDP information:
        Sending CDP packets every 60 seconds
        Sending a holdtime value of 180 seconds
        Sending CDPv2 advertisements is enabled
    ```

- `show cdp traffic` - displays traffic counters for CDP;
    ```IOS
	R1#show cdp traffic
	CDP counters:
	    Total packets output: 105, Input: 112
	    Hdr syntax: 0, Chksum error: 0, Encaps failed: 0
	    No memory: 0, Invalid packet: 0,
	    CDP version 1 advertisements output: 0, Input: 0
	    CDP version 2 advertisements output: 105, Input 112
    ```

- `show cdp interface [if]` - displays CDP enabled interface information;
    ```IOS
    R1#show cdp interface Gi0/0
    GigabitEthernet0/0 is up, line protocol is up
        Encapsulation ARPA
        Sending CDP packets every 60 seconds
        Holdtime is 180 seconds
    ```

- `show cdp neighbor [detail]` - displays information about active neighbors;
    ```IOS
    R1#show cdp neighbors
    Capability Codes: R - Router, T - Trans Bridge, B - Source Bridge
				      S - Swtich, H - Host, I - IGMP, r - Repeater,
					  P - Phone, d - Remote, C - CVTA, M - Two-port MAC
	Device ID   Local Intrfce   Holdtme   Capability Platform  Port ID
	SW1         Gig 0/0         153       R S I      2960      Gig 0/0
	R1          Gig 0/1         146       R B        ISR2911   Gig 0/0

	R1#show cdp neighbors detail
	-------------------------
	Device ID: SW1
	address(es):
		IP address: 171.68.162.134
	Platform: cisco 4500,  Capabilities: Router
	Interface: Ethernet0/1,  Port ID (outgoing port): Ethernet0
	Holdtime : 153 sec
	Version :
	Cisco Internetwork Operating System Software
	IOS (tm) 4500 Software (C4500-J-M), Version 11.1(10.4), MAINTENANCE INTERIM SOFTWARE
	Copyright (c) 1986-1997 by Cisco Systems, Inc.
	Compiled Mon 07-Apr-97 19:51 by dschwart
	```