Commonly used in conjunction with [[Spoofing|DHCP starvation]], the *DHCP Poisoning* is a technique to intercept traffic from an attacked host in order to read and/or manipulate the data in it.

It works by setting up a *Spurious DHCP Server* on the LAN and answering to DHCP requests as they come in. This malicious server gives the host the parameters it needs to connect to the LAN (congruent IP address and network mask) but sets up the default gateway as it's own IP address.

With this, any time the host needs to send traffic to the outside network, it will forward it to the attacker, instead of the actual gateway router. The attacker can then read contents of the message, alter it and then forward to the actual default gateway.