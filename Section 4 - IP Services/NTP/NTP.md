*Network Time Protocol* is a network protocol used to synchronize the clocks of devices through the network to ensure that every device has the same time and date. **NTP clients will request the time and date from NTP servers in a client-server fashion**.

NTP clients can also work as NTP servers, polling the time from one server, and serving that time and date to other clients. This increases the "distance" from the original **reference clock**. This distance is called **stratum**. Following this terminology:

- **Stratum 0 NTP servers** are the most precise source of time and date. They get their time from specialized atomic or GPS clocks. These are also called **Reference clocks**;
- **Stratum 1 NTP servers** get their time directly from reference clocks. Clients will only be able to connect to stratum 1 NTP servers or higher. These are also called **Primary servers**;
- **Stratum 2 - 15 NTP servers** are also called **Secondary servers**. They connect in a hierarchical format. Anything higher then stratum 15 is considered unreliable source.

> Also, "reference clock" can refer to a stratum 0 NTP server, or to the NTP server a client is polling the date and time from. For example, a stratum 2 NTP server could be the reference clock for a connected stratum 3 NTP server.

NTP servers higher then stratum 1 can also connect to each other on the same stratum to get a more precise time and date. These servers can operate in **server mode**, **client mode** and **symmetric active mode** (or all three at the same time).

> Example hierarchy of NTP servers:
> ![[Pasted image 20231031212630.png]]

