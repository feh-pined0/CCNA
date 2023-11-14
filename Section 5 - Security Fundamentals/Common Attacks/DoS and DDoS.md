A *Denial of Service* attack consists in preventing any type of service or device on the network to work properly. Generally, attacks of this type consist in overloading a device (usually a server) to the point where it cannot handle the basic tasks of the services it provides.

# DoS - SYN Message Flood

In a SYN message flood attack, an attacker will send numerous **[[TCP]] datagrams** with the SYN flag, indicating the will of a device to start a new TCP session. The server or device will then reply with the [[Three-way Handshake|SYN+ACK]] message, but the attacker will never answer this reply.

This causes the device to store a pending TCP connection in the TCP session table for a determined period of time. An because the attacker never responds and keeps sending TCP SYN messages, this table will overflow and the device will no longer be able to handle legit TCP sessions, causing it to be essentially offline.

# DDoS

*Distributed Denial of Service* attack is a more sophisticated approach to the DoS. This time, instead of only one device, the attacker infects multiple hosts with [[Malware|malware]] and have them all send SYN messages to a target, all at once. This greatly increases the threat's damage potential.

