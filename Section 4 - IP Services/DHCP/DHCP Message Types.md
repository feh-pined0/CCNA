The following message types are relevant for the CCNA:

## Sent by the server

- **OFFER**: used to offer a set of options to the requesting client. Can include IP addresses, default gateway, DNS servers, TFTP servers, etc.
- **ACK**: used to acknowledge the lease usage by the client;
- **NAK**: used to decline the lease usage by the client. It is the opposite of the ACK message;

## Sent by the client

- **DISCOVER**: broadcast by the client to discover available DHCP servers on the LAN;
- **REQUEST**: used to request the usage of a DHCP lease distributed by the server;
- **RELEASE**: used to tell the server the DHCP lease is no longer require and is not going to be used;
- **DECLINE**: used by the client to decline a DHCP offer from the server;

