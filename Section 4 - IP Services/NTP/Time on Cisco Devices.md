*Network Time Protocol* is used to exchange date and time information across multiple devices in order to make sure devices on the network have a synchronized time and date. This is important for various reasons: protocol operation, log dates, network stack functionality, etc.

Cisco devices have two internal clocks:

- A software clock, called "clock";
- A hardware clock, called "calendar";

Although different, these 2 clocks must be synchronized in order to guarantee normal device operation.

When a Cisco device connects and synchronizes time with and NTP server, the device itself becomes an NTP server, with stratum level of one plus the stratum level of the connected NTP server.

NTP servers with lower stratum levels are preferred by the OS.