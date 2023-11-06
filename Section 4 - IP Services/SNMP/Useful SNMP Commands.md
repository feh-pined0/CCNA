- `snmp-server [contact | location] [email | location]` - defines optional values for OIDs on this device;
```IOS
R1(config)# snmp-server contact fe_pinedo@gmail.com
```

- `snmp-server community <community-name> <ro|rw>` - configures a community string and the access level (read-only or read/write);
```IOS
R1(config)# snmp-server community enoSP12 rw
```

- `snmp-server host <nms-server> <version> <community-name>` - defines a NMS to manage this device, using the defined version and community string;
```IOS
R1(config)# snmp-server host 10.10.10.27 version 2c enoSP12
```

- `snmp-server enable traps <traps>` - enable the defined trap events to be captured and sent to the NMS;
```IOS
R1(config)# snmp-server host 10.10.10.27 version 2c enoSP12
```