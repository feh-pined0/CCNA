[[TCP]] and [[UDP]] are two transport layer (layer 4 in the OSI stack) protocols that provide host-to-host communication and data exchange. Although both aim to do the same thing, the way they do it differs a lot.

TCP is a connection oriented, reliable protocol, where data is sent and tracked to ensure that it was delivered on the other side of the connection. TCP spends a lot of resources trying to ensure that the data sent arrives at the other side in it's integral form, not losing any bits along the way.

UDP is a connection-less protocol, that tries to deliver the datagrams as fast as possible, while using minimal amount of resources. UDP is much simpler than TCP because it does not offer the same amount of services to the application that is using it, it simply sends the datagram without expecting to receive anything back or ensuring it arrived in "good form" at the other side.

Generally, TCP is used when a reliable data transfer is required, such as downloading a file, where the file needs to arrive 100% correct at the destination, while UDP is used in latency-sensitive contexts, such as when streaming a video or audio file though the network.

Although they are very different, UDP and TCP both keep track of sessions by using layer 4 addressing, also called *ports*. Ports are appended to the end of the IP address when being displayed (an example would be `10.0.0.67:443`, where "443" would be the layer 4 port). Some common ports are: 

|        TCP       |        UDP         | UDP & TCP |
| ---------------- | ------------------ | --------- |
| FTP Data (20)    | DHCP Server (67)   |  DNS (53) |
| FTP Control (21) | DHCP Client (68)   |           |
|     SSH (22)     |     TFPT (69)      |           |
|    Telnet (23)   | SNMP Agent (161)   |           |
|    SMTP (25)     | SNMP Manager (162) |           |
|    HTTP (80)     | Syslog (514)       |           |
|    HTTPS (443)   | SNMP Agent (161)   |           |

