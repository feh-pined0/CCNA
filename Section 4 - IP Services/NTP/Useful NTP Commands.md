These commands can be useful when trying to configure NTP on Cisco devices:

- `clock set <hh:mm:ss> [<1-31>|MONTH] <1993-2035>` - manually configures the software clock of the device. **MUST BE APPLIED FROM THE ELEVATED TERMINAL** (not from config mode);
```IOS
R1# clock set 20:35:00 31 Oct 2023
R1# show clock detail
20:35:05.887 UTC Tue 31 2023
Time source is user configuration
```

- `calendar set <hh:mm:ss> [<1-31>|MONTH] <1993-2035>` - manually configures the hardware clock of the device. **MUST BE APPLIED FROM THE ELEVATED TERMINAL** (not from config mode);
```IOS
R1# calendar set 20:35:00 31 Oct 2023
R1# show calendar
20:35:05 UTC Tue 31 2023
```

- `clock read-calendar` - configures the software clock to be synchronized with the hardware clock. **MUST BE APPLIED FROM THE ELEVATED TERMINAL** (not from config mode);
```IOS
R1# show clock
00:00:15.578 UTC Mon Sep 6 1993
R1# show calendar
14:55:07 UTC Sun Dec 27 2020
R1# clock read-calendar
R1# show clock
14:55:07.522 UTC Sun Dec 27 2020
```

- `clock update-calendar` - configures the hardware clock to be synchronized with the software clock. **MUST BE APPLIED FROM THE ELEVATED TERMINAL** (not from config mode);
```IOS
R1# show calendar
00:00:15 UTC Mon Sep 6 1993
R1# show clock
14:55:07.124 UTC Sun Dec 27 2020
R1# clock update-calendar
R1# show calendar
14:55:07 UTC Sun Dec 27 2020
```

- `clock timezone <name> <hours-offset (-23 - 23)> [minutes-offset]` - configures the timezone offset of the system clock;
```IOS
R1(config)# clock timezone GMT -3
```

- `clock summer-time recurring <name> <start> <end> [offset]` - configures a recurring summer-time daylight saving on the device;
	- This example configures a recurring daylight saving every year, starting on the first Friday of the fourth week of December, at 10 pm and ending on the first Wednesday of the fourth week of March at 00:00 am;
```IOS
R1(config)# clock summer-time recurring DLS 4 Friday December 22:00 4 Wednesday 00:00 March
```

- `ntp server <x.x.x.x> [prefer]` - configures a NTP server for the device to query for date and time. The `prefer` keyword makes that specific server preferable for queries. Multiple servers can be configured with the same command;
```IOS
R1(config)# ntp server 216.239.35.0 prefer
R1(config)# ntp server 216.239.35.4
R1(config)# ntp server 216.239.35.12
```

- `ntp update-calendar` - configures the hardware clock to update with NTP server information;
```IOS
R1(config)# ntp update-calendar
```

- `ntp source <interface>` - configures the device's NTP server to respond to NTP requests from the selected interface;
```IOS
R1(config)# ntp source loopback0
```

- `ntp master [<1-15>]` - configures the device to act as an NTP master server, even if it is not synchronized to any other NTP server. It uses the selected stratum level, or the default value (8);
```IOS
R1(config)# ntp master
R1(config)# do show ntp associations

  address         ref clock    st  when  poll  reach   delay   offset    disp
*~127.127.1.1     .LOCL.        7     2    64    377   0.000    0.000   0.292
 * sys.peer, # selected, + candidate, - outlyer, x falseticker, ~ configured
```

- `ntp peer <x.x.x.x>` - configures a NTP peer to help the device synchronize the time;
```IOS
R1(config)# ntp peer 10.0.23.2
```

- `show ntp associations` - displays configured NTP servers information;
```IOS
R1# show ntp associations

  address         ref clock    st  when  poll  reach   delay   offset    disp
*~216.239.35.0    .GOOG.        1    22    64      1  50.637    1.087  939.58
 ~216.239.35.4    .GOOG.        1    19    64      1  60.279   -4.402  939.83
 ~216.239.35.12   .GOOG.        1    20    64      1  63.205  1351.20  938.34
 * sys.peer, # selected, + candidate, - outlyer, x falseticker, ~ configured
```

- `show ntp status` - displays statistics of the NTP protocol on the device;
```IOS
R1# show ntp status
Clock is synchronized, stratum 2, reference is 216.239.35.0
nominal freq is 1000.0003 Hz, actual freq is 999.5003 Hz, precision is 2**14
ntp uptime is 295800 (1/100 of seconds), resolution is 1001
reference time is E393F0A9.1F758C5B (05:50:33.122 UTC Mon Dec 28 2020)
clock offset is 1343.7280 msec, root delay is 49.13 msec
root dispersion is 2275.31 msec, peer dispersion is 3.44 msec
loopfilter state is 'SPIK' (Spike), drift is 0.000499999 s/s
system poll interval is 64, last update was 173 sec ago.
```

