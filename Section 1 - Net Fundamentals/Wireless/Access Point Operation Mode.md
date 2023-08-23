  Access points can operate in other modes other than the default, according to the network needs:

- **Repeater**: the [[Access Points|access point]] will connect to another access point (with wireless), and repeat the signals sent from it. This can increase the [[Wireless Signal|signal range]], but generally degrades signal and affects performance;
- **WGB** (*Workgroup Bridge*): in WGB mode, a AP will connect to a client (like a PC for example) with a wire, and connect itself to the internet with wireless. This can be used to:
	- Connect clients that do not have wireless capabilities to a wireless network;
	- Extend the signal range of a wireless network;

Also, they (access points) can be categorized in the operation mode type:

- **Autonomous AP**: the AP works independently of other devices. It gets connected directly (or using one of the above methods) to the wired network with a trunk uplink and associates it's BSSs traffic with one or more VLANs.
	- These can be used in small networks, but the labor of configuring each AP and each device on the network to use these VLANs is quite heavy.
- **Lightweight AP**: the AP works in conjunction with a [[Controllers (WLC & Cisco DNA Center)|WLC]]. It uses [[CAPWAP]] protocol to authenticate with the WLC and then forwards all traffic to it, which in turn forwards traffic in the wired and wireless network.
	- This is also called a **Split-MAC Architecture**, because the functionality of the AP is split between itself (physical capabilities such as RF transmission of the frames) and the WLC (authentication and association, forwarding traffic, etc).

Also, LWAPs can operate in other modes:

- **Local**: default operation. The AP offers one or mode BSS for clients to connect, based on WLC configuration;
- **FlexConnect**: like the default operation, but in case traffic from AP to WLC cannot happen, the AP will act as a autonomous AP, forwarding traffic locally;
- **Sniffer**: the AP will act as a packet sniffer (for 802.11 frames), sending packet data and analysis to a server. It does not provide connectivity for clients (no BSS).
- **Monitor**: the AP will analyze 802.11 frames to try and detect rogue devices. If it is detected, the AP will send de-authentication messages for the WLC in order to disassociate the device from the wireless network;
- **Rogue Detector**: Like monitor, but instead of analyzing 802.11 frames, it listens on the physical wire;
- **Bridge/Mesh**: the AP will act like a bridge, connecting to other APs and forming a bridge or mesh to another sites or locations, in case copper or fiber wires are difficult to deploy;
- **Flex plus Bridge**: Same as bridge/mesh, but adds FlexConnect capabilities.

There is also a third operation mode type, which is called **Cloud-based AP**. Here, APs will be managed and configured using a cloud solution (kinda like a cloud based WLC, such as Cisco Meraki), but network data traffic itself will be forwarded from the AP. This falls in between autonomous AP and LWAPs.