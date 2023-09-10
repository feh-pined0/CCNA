STP has many standards. Some were developed by the IEEE, and some by Cisco (proprietary);

## IEEE STP standards

- **STP** \[802.1D\] (*Spanning Tree Protocol*): the original, [[Classic STP|classic STP]];
- **RSTP** \[802.1w\] (*Rapid Spanning Tree Protocol*): a upgraded version of STP, it was designed to be much faster when adapting to network topology changes (that in classic STP, could take up to 50 seconds);
- **MSTP** \[802.1s\] (*Multiple Spanning Tree Protocol*): it is almost the same as RSTP, with the addition of the possibility to use multiple instances of RSTP for each [[802.1Q Header|VLAN]] or group of VLANs;

## Cisco STP standards

- **PVST+** (*Per-VLAN Spanning Tree*): it was originally created after the standard 802.1D STP. It runs an STP instance for each VLAN on the switch. The "plus" is because the original PVST only ran with ISL encapsulation, while the plus version runs on dot1q encapsulation;
- **RPVST+** (*Rapid Per-VLAN Spanning Tree*): an upgrade to the original PVST+, based on the 802.1w standard, it is a faster version of the original protocol;