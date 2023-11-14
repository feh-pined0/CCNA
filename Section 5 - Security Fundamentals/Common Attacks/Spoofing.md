In spoofing attacks, an attacker will use spoofed (stolen/made up) addresses (layer 2 MAC, layer 3 IP and layer 4 ports) to take advantage of vulnerabilities. Spoofing by itself is an exploit to many vulnerabilities.

# DHCP Spoofing

In DHCP spoofing, an attacker will spoof many MAC addresses and, for each one, will request a [[DHCP|DHCP lease]]. The attacker will not complete the DHCP lease process, but DHCP offers make so that the DHCP server does not lease the "reserved" IP address for a while. With this, an attacker can exhaust a DHCP pool very quickly, preventing new devices to join the network.

