These commands can be useful when trying to configure remote access on Cisco devices:

- `enable <[password|secret]> <WORD>` - sets a password prompt to be displayed when trying to enable a terminal;
	- `secret` makes so that the password will be encrypted when displayed using `show running-config`;
```IOS
R1(config)# enable secret #$tgs256@last7*
```

- `username <user> secret <password>` - creates new access credentials for user `user`. Can be used to authenticate access to the device;
```IOS
R1(config)# username fe_pinedo secret #$tgs256@last7*
```

- `line vty <[line|line-range]>` - enters the *Virtual TeleType* configuration mode, for a specific line or a range of lines;
	- It is good practice to configure all lines equally. Default devices have lines $0$ through $15$;
```IOS
R1(config)# line vty 0 15
R1(config-line)#
```

- `login local` - configures the line to require username + password credentials when accessing it;
```IOS
R1(config-line)# login local
```

- `exec-timeout <minutes> <seconds>` - configures a session to expire in a defined amount of time;
```IOS
R1(config-line)# exec-timeout 5 0
```

- `transport input <[all|none|telnet|ssh]>` - enables remote access using the specified protocols;
```IOS
R1(config-line)# transport input ssh
```

- `access-class <acl> in` - enables remote access from hosts defined on a access-list;
```IOS
R1(config-line)# access-class 1 in
```

- `ip ssh version <[1|2]>` - restrict SSH sessions to use version 1 or 2 only;
```IOS
R1(config)# ip ssh version 2
```

- `crypto key generate rsa` - generates a asymmetric key pair for this device and implicitly enables SSH;
```IOS
R1(config)# crypto key generate rsa
The name for the keys will be: R1.atiweb.intranet
  Choose the size of the key modulus in the range of 360 to 4096 for your General
  Purpose Keys. Choosing a key modulus greater than 512 may take a few minutes.

How many bits in the modulus [512]: 2048
% Generating 2048 bit RSA keys, keys will be non-exportable...
[OK] (elapsed time was 1 seconds)

R1(config)#
*Nov 07 16:21:57.778: %SSH-5-ENABLED: SSH 1.99 has been enabled
```

- `no ip ssh server authenticate user password` - configures SSH to not authenticate using username and password credentials;
```IOS
R1(config)# no ip ssh server authenticate user password
```

- `ip ssh pubkey-chain` - enters SSH public key configuration mode;
```IOS
R1(config)# ip ssh pubkey-chain
R1(config-ssh-pubkey)#
```

- `username <user>` - enters SSH public key configuration for user mode;
```IOS
R1(config-ssh-pubkey)# username fe_pinedo
R1(config-ssh-pubkey-user)#
```

- `key-string` - enters public key string prompt mode, where a user can input it's public key for PK SSH authentication;
```IOS
R1(config-ssh-pubkey-user)# key-string
R1(config-ssh-pubkey-data)#
```

