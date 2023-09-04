*Port Aggregation Protocol* is a Cisco proprietary protocol that automatically manages and forms [[EtherChannel|port-channels]] between devices. It is very similar to the industry standard [[LACP]], with the only difference that it is not common to all devices from different vendors, and the commands for setting it up are a little different:

To configure PAgP on a Cisco device:

- Select the interface range to form the port-channel:
```IOS
ASW1(config)# interface range g0/0 - 3
ASW1(config-if-range)#
```

- Apply the `channel-group [group-num] mode [desirable|auto]` command to select the protocol and mode:
```IOS
ASW1(config-if-range)# channel-group 1 mode desirable
Creating a port-channel interface Port-Channel 1
```

Note two things:
> When creating a channel group, a port-channel logical interface is automatically created.

and
> Desirable mode sets the port-channel to form with the other device if it's configuration is desirable or auto. Auto mode configures the port-channel to only form if the other device is set to desirable.

