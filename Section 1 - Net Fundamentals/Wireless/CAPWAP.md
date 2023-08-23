*Control and Provisioning of Wireless Access Point* is a protocol for handling connections between an [[Access Point Operation Mode|lightweight access point]] and a [[Controllers (WLC & Cisco DNA Center)|WLC]]. It serves as the foundation for configuring and forwarding data for LWAPs.

When using CAPWAP, access points are connected to the wired network with an access port, on the same broadcast domain as the WLC. The AP then "searches" for the WLC and present it's [[X.509 certificate]] to ingress the wireless network. The WLC then appends the LWAP to the network and provides configurations for the device, as well as it's advertised BSSs and other parameters.

Data between LWAP and WLC are exchanged using two tunnels:

- **Control Tunnel**: using port UDP 5246, this tunnel is used to provide configuration and manage the AP. Traffic is encrypted using the X.509 certificates by default;
- **Data tunnel**: using port UDP 5247, this tunnel is used to forward traffic received from wireless clients to the WLC, and vice-versa. The APs **do not** forward traffic directly to the wired network. It **must** go through the WLC.