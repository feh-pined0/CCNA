A *Service Set* is a set or group of devices that all share the same SSID (*Service Set Identifier*). When two devices share the SSID, they are connected to the same network.

A service set can be of 3 types (as defined by the IEEE 802.11 standard):

- Independent;
- Infrastructure;
- Mesh;

Some implementations of these types of service sets are:

- **IBSS** (*Independent Basic Service Set*): consists of two or more devices connected directly to each other without the use of an access point.
- **BSS** (*Basic Service Set*): consists of network with a basic infrastructure. In this case, an AP is used to provide connectivity between peers. Here two IDs are defined:
	- The BSSID identifies the AP on the network (this is the same as the MAC address of the AP);
	- The SSID identifies the network itself (and is human-readable);
  In the definition there is also the BSA (Basic Service Area), which denotes the active radio frequency area in which the AP provides network connectivity;
- **ESS** (*Extended Service Set*): here multiple APs are connected by a wired network. Each AP forms a BSS, which all share the same SSID. BSSs use different RF channels to avoid interference and each BSS have its BSSID. This configuration allows for all APs to appear as a single entity for clients, thus enabling seamless and transparent wireless networks (this is called **roaming**). The following image ilustrates this topology:

    ![[Extended Service-Set.png]]
    
- **MBSS** (*Mesh Basic Service Set*): here multiple APs (**MAPs** *Mesh Access Points*) connect to each other directly, forming a "mesh" of wireless connectivity. This mesh is then connected by a single AP (the **RAP** *Root Access Point*) to a wired network which serves as the backbone of the wireless net. APs in mesh networking need to have at least two radios: one to connect to end clients, and one to connect to the mesh.
    
    ![[Wireless Mesh.png]]

The following 802.11 standards are defined:

![[Wireless Standards.png]]

