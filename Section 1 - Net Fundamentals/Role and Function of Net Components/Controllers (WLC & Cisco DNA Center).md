A WLC (Wireless LAN Controller) is responsible for managing all the wireless connections to the network. This generally includes the VLAN access, general switching / packet encapsulation and proxies for all traffic coming from wireless access points ([[Access Points|WAPs]]) and wireless clients (such as cell phones, notebooks, etc). Practically speaking, WLCs provide all the configuration parameters for WAPs, like passwords and SSIDs and encapsulate and forward traffic (through [[CAPWAP]] tunnels).

WLCs can be deployed in four models into the network:

- **Unified**: the WLC is a dedicated hardware appliance, centralizing the wireless data management. This approach generally supports up to 6000 APs;
- **Cloud-based**: the WLC is a [[Virtual Machine|VM]] running on a [[On Premises and Cloud|cloud server]]. Supports up to 3000 APs;
- **Embedded**: the WLC is integrated with a [[Switches|switch]] on the physical network. Supports up to 200 APs;
- **Cisco Mobility Express**: the WLC is integrated with an AP on the physical network. Supports up to 100 APs;

Also, when talking about WLCs and wireless networks in general ([[802.11 Messages|802.11]] and [[Authentication Methods|802.1x]]), the terms *interface* and *ports* do have different meanings, as "port" refers to the physical port on the device, and "interface" refers to a virtual interface (kinda like an [[SVI]]):

- **Management Interface**: one of the first interfaces to be configured, it is used for management traffic such as telnet, SSH, HTTP and HTTPS, RADIUS, authentication, etc. Also, CAPWAP tunnels are formed to this interface;
- **Redundancy Management Interface**: when connecting two WLCs for [[HA]], one of them becomes the active and is managed via the management interface, and the other becomes "standby" and is managed via the redundancy management interface;
- **Virtual Gateway Interface**: it is used for communicating directly with wireless clients, such as when forwarding DHCP requests (DHCP relay) and authenticating stations via web interfaces. This interface's IP **must** use an IP address that is not on any subnet on the network;
- **Service Port Interface**: if the Service Port (physical) is used, this interface is created for out-of-band management (this separates management on a physical layer).
- **Dynamic Interface**: this is used to map a WLAN to a VLAN on the network;

Cisco DNA Center can be a software or appliance solution for network managing, analysis and monitoring. DNA Center is a network controller that does lots of things, such as monitoring the network, providing configurations and images to network devices (automation), smart network analysis through AI and Machine Learning, managing QoS and security through group policies and much more. It does all this with intent-based architecture, which is a form of building complex networks with tons of configurations and policies, while inputting to the software the business intent for the network.

In general, network controllers serve an important role for managing different aspects of the network, providing a way for configuring lots of devices in a way that is not overwhelming.