*Link Layer Discovery Protocol* is a layer 2, industry standard [[Discovery Protocols|discovery protocol]] created after Cisco's [[CDP]].

It operates basically the same as CDP, but there are some key differences:

- It uses multicast MAC address `0180.C200.000E` to send LLDP messages;
- The default timer for sending messages is **30 seconds**;
- The default hold-time for LLDP table information is **120 seconds**;

Also, LLDP has another timer: the initialization timer. It defines how long after the `lldp run` command should the service actually start sending LLDP messages.

"Show" commands are also the same as CDP, just with LLDP in the front.

Finally, LLDP is disabled by default on Cisco devices. Turning it on requires for it to be enabled on the global context, by issuing `lldp run` on global configuration, and then enabling it on a per interface basis, using the `lldp transmit` and `lldp receive` commands to transmit and receive LLDP frames, respectively.