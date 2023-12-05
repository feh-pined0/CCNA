Device passwords and users are defined to allow access to different **privilege levels** on the device. These privilege levels define which commands are accessible to a user currently in that mode.

The more common modes are:
- **Privilege Level 0**: in this mode, the user can only logout of the device, exhibit a list of commands or attempt to enable a higher privilege mode;
- **User EXEC Mode** (level 1): in this mode, some show commands are available for the user;
- **Privileged EXEC Mode** (level 15): in this mode, the user has access to all of the device's functions, including configuration commands;

To assess the current privilege level for a session, simply administer the `show privilege` command. To attempt to enable a higher privilege mode, administer the `enable <privilege>` command. Using the `enable` command without a privilege will try to log on with the highest privilege level (15).

