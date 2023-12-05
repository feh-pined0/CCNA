Local passwords and credentials can be configured to be required in order for device management to be done. These local credentials [[RADIUS|exist only on the device]].

## Enable credentials

Credentials for enabling a terminal (i.e. entering privileged EXEC mode) can be set using the commands:
- `enable password <security-level> <WORD>`: configures a password either in plain text, or hashed using a algorithm determined by the security level specified;
- `enable secret <WORD>`: configures a password that is encrypted in the device's configuration. When using this in conjunction with the command above, only the former will work (`enable secret` overrides `enable password`, even if both are shown in the device's configuration);

## Usernames and Login

A login can be configured to be required using a password or a username + password combo.

This configuration is done in a "line" basis. This means that a different configuration can be applied to the console port and the [[Terminal Emulators|vty]] lines.

To configure this:

1. Select the lines to apply a configuration:
```IOS
R1(config)# line console 0
R1(config-line)#
```

2. Apply the `password <security-level> <WORD>` command:
```IOS
R1(config-line)# password CISCO
R1(config-line)#
```

3. Finally, apply the `login` command to require a login to enter user EXEC mode:
```IOS
R1(config-line)# login
R1(config-line)#
```

4. Additionally, if a username + password credential set is desired, first configure that using the `username` command from global configuration mode:
```IOS
R1(config)# username <username> password <security-level> <WORD>
R1(config)#
```

5. Then, instead of applying the `login` command on the desired line, apply the `login local` command;
```IOS
R1(config-line)# login local
R1(config-line)#
```

## Password Encryption Service

A additional service can be enabled on the device to encrypt all passwords on the configuration. For this, just apply the `service password-encryption` command from global configuration mode. Then, any passwords that are in plain text in configuration will automatically be encrypted.

