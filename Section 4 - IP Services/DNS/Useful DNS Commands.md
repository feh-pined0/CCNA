These commands are useful when trying to configure DNS on Cisco devices:

- `ip dns server` - configures the device to operate as a DNS server, resolving queried DNS names.
```IOS
R1(config)# ip dns server
```

- `ip host <dns-name> <ip-address>` - configures a DNS mapping from the DNS name to an IP address.
```IOS
R1(config)# ip host R1 10.0.10.1
R1(config)# ip host PC01 10.0.10.15
```

- `ip name-server <dns-server>` - configures a DNS server on the device. It will then use this configured server to perform queries when needed.
```IOS
R1(config)# ip name-server 8.8.8.8
R1(config)# ip name-server 8.8.0.0
```

- `ip domain name <domain-name>` - configures the router's domain name. This is the administration domain the router is in. It will include this domain name in any DNS resolve that does not specify one.
```IOS
R1(config)# ip domain name atiweb.com.br
```
```Powershell
C:/Users/root> ping R1
Pinging R1.atiweb.com.br [172.217.25.110] with 32 bytes of data:
```

- `ip domain lookup` - configures the device to actually perform DNS queries.
	- Even if a name server is configured with the `ip name-server` command, the device will not perform queries if this command is not administered;
```IOS
R1(config)# ip domain lookup
```

- `show hosts` - displays information about DNS mappings such as cache, entry age, type, etc.
```IOS
R1# show hosts

Default domain is not set
Name/address lookup uses domain service
Name servers are 8.8.8.8 8.8.0.0
Codes: UN - unknown, EX - expired, OK - OK, ?? - revalidate
       temp - temporary, perm - permanent
       NA - Not Applicable, None - Not defined

Host              Port   Flags         Age   Type   Address(es)
youtube.com       None   (temp, OK)    0     IP     172.217.25.110
R1                None   (perm, OK)    0     IP     10.0.10.1
PC01              None   (perm, OK)    0     IP     10.0.10.15
```