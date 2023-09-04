*Link Aggregation Control Protocol* is a industry-standard port-channel protocol that handles multiple link aggregation. It is defined in the [IEEE 802.3ad](https://www.ieee802.org/3/hssg/public/apr07/frazier_01_0407.pdf).

LACP does auto-negotiation of [[EtherChannel|etherchannel]] (creation and maintenance). This ensures that the port-channel is not only created between two devices, but if anything is abnormal on the port-channel environment (such as [[Collisions and Errors|duplex/speed mismatch]] between physical interfaces of the same group), the device works to fix it by either adjusting any configuration or straight up removing the problematic interface from the group.

To configure LACP on a Cisco device:

- Select the interface range to form the port-channel:
```IOS
ASW1(config)# interface range g0/0 - 3
ASW1(config-if-range)#
```

- Apply the `channel-group [group-num] mode [active|passive]` command to select the protocol and mode:
```IOS
ASW1(config-if-range)# channel-group 1 mode active
Creating a port-channel interface Port-Channel 1
```

Note two things:
> When creating a channel group, a port-channel logical interface is automatically created.

and
> Active mode sets the port-channel to form with the other device if it's configuration is active or passive. Passive mode configures the port-channel to only form if the other device is set to active.

