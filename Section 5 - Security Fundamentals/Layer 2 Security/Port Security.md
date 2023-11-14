*Port Security* is a layer 2 security feature that restricts which MAC addresses are allowed to send traffic to an interface on a switch. It can limit a certain switchport to only allow one or two addresses, or to allow only the first learned address.

Port security is configured on a per-interface basis:

```IOS
SW1(config)# interface FastEthernet0/1
SW1(config-if)#
```

Then, statically configuring the switchport mode:

```IOS
SW1(config-if)# switchport mode access
```

Finally, activating port security:

```IOS
SW1(config-if)# switchport port-security
```

The default configuration for this command is to activate port-security on the interface with a violation mode of `shutdown`, no age timer and a maximum MAC address counter of 1:

```IOS
SW1# show port-security interface fa0/1

Port Security              : Enabled
Port Status                : Secure-up
Violation Mode             : Shutdown
Aging Time                 : 0 mins
Aging Type                 : Absolute
SecureStatic Address Aging : Disabled
Maximum MAC Addresses      : 1
Total MAC Addresses        : 0
Configured MAC Addresses   : 0
Sticky MAC Addresses       : 0
Last Source Address:Vlan   : 0000.0000.0000:0
Security Violation Count   : 0
```

Here, some things are important:

- `Port Status`: defines the current status of the port.
	- `Secure-up` means that port security is enabled, and that the port is up and forwarding;
	- `Secure-shutdown` means that port security is enabled, and that the port is down;
		- Ports in this state are put in an `err-disabled` state by the device;
- `Violation Mode`: defines the default behavior for when a violation of port security is detected;
	- `Shutdown`: on violation, puts the port in an `err-disabled` state;
	- `Restrict`: on violation, discards traffic from the port indefinitely or until the age timer has reached zero;
		- **The interface is not disabled**;
	- `Protect`: same as `Restrict` but does not log the event to syslog and does not increase the violation counter (it's like a silenced restrict);
- `Aging Time`: the timer configured for a MAC address(es) to expire;
- `Aging Type`: the type of the configured timer;
	- `Absolute` means that, once the timer is expired, the MAC address of the interface will be cleared;
		- This cleared MAC address can be relearned as soon as it's cleared;
	- `Inactivity`: means that the timer will reset each time the switch receives a frame from this MAC address;
- `SecureStatic Address Aging`: disabled by default. If enabled, makes statically configured port-security MAC addresses to age as well;
- `Sticky MAC Addresses`: these are MAC addresses that are dynamically learned by the port-security process and will stick to the configuration (behaving like a statically configured one);

# MAC Address Table Relation

Addresses learned from interfaces with port-security enabled will have different entries depending on the method used by the port-security process:

- **Sticky and Static** will have a type of **STATIC**;
- **Dynamically Learned** will have a type of **DYNAMIC**;

# Automatic Error Recovery

When a port violation happens, the port-security process defaults to disabling the interface and requiring a manual re-enable. An automatic recovery of the port can be configuring using the `errdisable recovery cause` command:

```IOS
SW1(config)# errdisable recovery cause psecure-violation
```

\*This works for any process that can put an interface in an err-disabled state.

The default recovery timer is **300 seconds**. Can be configured with the `errdisable recovery interval <seconds>`.

