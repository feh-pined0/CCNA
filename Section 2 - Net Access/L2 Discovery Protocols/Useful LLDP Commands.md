- `show lldp` - displays information about CDP timers, and informs if CDP is enabled/disabled;
    ```
    R1#show lldp
    Global LLDP information:
        LLDP advertisements are sent every 30 seconds
        LLDP hold time advertised is 120 seconds
        LLDP interface reinitialisation delay is 2 seconds
    ```

- `show lldp traffic` - displays traffic counters for CDP;
    ```IOS
	R1#show lldp traffic
	LLDP traffic statistics:
	    Total frames out: 4
	    Total entries aged: 0
	    Total frames in: 3
	    Total frames received in error: 0
	    Total frames discarded: 0
	    Total TLVs discarded: 0
	    Total TLVs unrecognized: 0
    ```

- `show lldp interface [if]` - displays CDP enabled interface information;
    ```IOS
    R1#show lldp interface Gi0/0
    GigabitEthernet0/0:
	    Tx: enabled
	    Rx: enabled
	    Tx state: IDLE
	    Rx state: WAIT FOR FRAME
    ```

- `show lldp neighbor [detail]` - displays information about active neighbors;
    ```IOS
    R1#show lldp neighbors
    Capability Codes:
        (R) Router, (B) Bridge, (T) Telephone, (C) DOCSIS Cable Device
        (W) WLAN Access Point, (P) Repeater, (S) Station, (O) Other
        
	Device ID   Local Intf   Holdtme   Capability Platform  Port ID
	SW1         Gig 0/0      120       R B        2960      Gi0/0
	R1          Gig 0/1      120       R          ISR2911   Gi0/0

	R1#show lldp neighbors detail
	-------------------------
	Chassis id: 0002.4A13.6C01
	Port id: Gig0/0
	Port Description: GigabitEthernet0/0
	System Name: SW1
	System Description:
	Cisco IOS Software, C2960 Software (C2960-UNIVERSALK9-M), Version 15.1(4)M4, RELEASE SOFTWARE (fc2)
	Technical Support: http://www.cisco.com/techsupport
	Copyright (c) 1986-2012 by Cisco Systems, Inc.
	Compiled Thurs 5-Jan-12 15:41 by pt_team
	Time remaining: 90 seconds
	System Capabilities: R B
	Enabled Capabilities: R B
	Management Addresses - not advertised
	Auto Negotiation - supported, enabled
	Physical media capabilities:
	1000baseT(FD)
	100baseT(FD)
	Media Attachment Unit type: 10
	Vlan ID: 1

	Total entries displayed: 1
	```