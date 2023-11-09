These commands can be useful when using a Cisco device's file system:

- `show flash` - displays the contents of flash memory.
```IOS
R1# show flash

System flash directory:
File   Length    Name/status
  3    33591768  c2900-universalk9-mz.SPA.151-4.M4.bin
  2    28282     sigdef-category.xml
  1    227537    sigdef-default.xml
[33847587 bytes used, 188304645 available, 222152232 total]
249856K bytes of processor board System flash (Read/Write)
```

- `show file systems` - displays the available file systems.
- `copy <source> <destination>` - copies a file from source to destination.
```IOS
R1# copy flash:text.txt flash:copiedtext.txt
```

- `delete <file-path>` - deletes a file from the system.
```IOS
R1# delete flash:text.txt
```

- `write memory` - saves configuration to nvram.
```IOS
R1# write memory
Building configuration...
[OK]
```

- `boot system <image-path>` - makes the device boot from the specified image.
```IOS
R1(config)# boot system flash:c2900-universalk9-mz.SPA.151-4.M4.bin
```

- `ftp username <user>` - defines the username to use when connecting to FTP servers.
```IOS
R1(config)# ftp username default
```

- `ftp password <password>` - defines the password to use when connecting to FTP servers.
```IOS
R1(config)# ftp password passwd
```

