- `logging console <level|WORD>` - configures the logging level for the console line. Default is 7 and enabled by default;
```IOS
R1(config)# logging console informational
```

- `logging monitor <level|WORD>` - configures the logging level for the monitor line. Default is disabled by default;
```IOS
R1(config)# logging monitor notification
```

- `logging buffered <buffer-size(bytes)> <level|WORD>` - configures the logging level and size for the RAM buffer;
```IOS
R1(config)# logging buffered 8192 6
```

- `logging [host] <host>` - configures logging on an external server;
```IOS
R1(config)# logging 192.168.1.100
```

- `logging trap <level|WORD>` - configures the logging level for the external server;
```IOS
R1(config)# logging trap warning
```

- `terminal monitor` - enables console logging on this VTY, with the level configured with `logging monitor` command;
```IOS
R1# terminal monitor
```

- `service timestamps log <datetime|uptime>` - configures the timestamp for the syslog messages to use date-time or system uptime;
```IOS
R1(config)# service timestamps log datetime
```

- `[no] service sequence-numbers` - enables or disables sequence numbers on syslog messages;
```IOS
R1(config)# no service sequence-numbers
```

