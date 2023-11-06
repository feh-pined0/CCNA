Syslog is an open standard and protocol for logging and keeping track of events that occur on the device. Cisco devices such as routers and switches run syslog by default.

These logs can be accessed by a number of different locations, being useful when debugging and troubleshooting problems.

The default format for a Syslog message is as follows:

`<seq>: <timestamp>: %<facility>-<severity>-<mnemonic>: <description>`

Where:

- `seq`: the sequence number of the message. Increases by one on each message logged;
- `timestamp`: the date-time or system uptime on the event occurrence;
- `facility`: the process which generated the log message (such as OSPF, LINK, SYS, etc);
- `severity`: the [[Syslog Severity Levels|severity level]] of the event;
- `mnemonic`: a short label of the event;
- `description`: a description of the event;

Here is an example of a syslog message:

`000041: Feb 11 03:02:56.305: %LINK-3-UPDOWN: Interface GigabitEthernet0/1, changed state to up`

Syslog can be accessed locally (through the serial interface of the device) or remotely (either by the virtual terminal created by protocols such as SSH or Telnet, or by a dedicated server);

Syslog external servers will listen to syslog messages on the **UDP/514** port.