When discussing about network security regarding network components, things like [[Asymmetric Key Pairs|asymmetric key authentication]], users and passwords are always top priority. But networking devices have a security flaw that can be easily overlooked when deploying such device: **the console port**.

This port comes with no security at all by default and, as long as a user has physical access to the device, accessing it is just a matter of plugging in a cable.

Cisco devices can be configured to require a password for the console port to be enabled, or a username + password credential set, to authenticate console port usage.

This can be done by:

1. Accessing the console line configuration with `line console 0`;
2. Administering the `login` or `login local` command;
3. The `login` command make so that to use the console port, users must have the console port password, configured with the `password` command/
4. The `login local` command makes so that to use the console port, users must authenticate with a username + password, defined using the command `username <user> secret <password>` command from the global config mode;

