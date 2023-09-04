When separating different types of network, there are two major groups of networks that can be defined: LAN and WAN. The Local Area Network is confined to a “small” physical space (this “small” can actually be quite big, like a campus or a branch office, for example) and typically represents only a segment of an enterprise network. When a company has multiple network segments, generally separated by a large physical space, these segments need to have a communication channel between them. Not only that, but they also need to reach public services (such as a [[On Premises and Cloud|cloud]] provider) in order to make available all the needed tools for their business to work properly. Think of this as a company that has multiple branch offices for example, and they need to communicate with a specific data-center in order to access a VoIP server or a web application. For this, they would make a Wide Area Network.

The internet is generally the main topic when talking about this, but WANs are actually any network topology that connects two or more LANs between a large physical space. For this, you could use the internet (as it’s being done today, with VPNs and virtual site-to-site tunnels), but you could also use other types of technology to connect these LANs. Some examples are:

- **VPN**: The most modern WAN connections will make use of a topology called SD-WAN in order to connect branch sites to each other. *Software Defined WAN* makes use of VPN to connect these sites through a normal, readily available, fast ethernet connection provided through an ISP. The traffic goes through the public internet, encrypted, to the branch and cloud locations and it is a cheap way to have a QoS implemented WAN. SD-WAN also makes the WAN more manageable by centralizing control of site devices.
- **Leased Lines**: Not used as much today, these lines are used to connect remote offices and customers directly to the ISP or another remote office. Because this is used to cover large distances, the ISP also provides devices in the middle to assure data is going through just fine. The leased lines are exclusive to the customer and are not shared between multiple customers, making this a reliable and fast connection. Although, it is a very expensive solution and was first replaced by MPLS.    
- **MPLS**: The *Multi-Protocol Label Switching* is a method to connect LANs by providing a dedicated set of paths (a mesh) in which frames can travel to and from these LANs using the MPLS protocol. Besides providing this dedicated mesh (it can be shared between customers or private to a specific customer), MPLS can also label packets with QoS information, to ensure that priority data (such as voice) gets [[Frame Switching|switched]] as fast as possible between the ingress edge router and the egress edge router.

These are some examples. The WAN architecture has a lot of possible topologies, and it depends on the customer needs when deciding which solution to use. Some older alternatives are Frame Relay, ATM (Asynchronous Transfer Mode) and ISDN (Integrated Services Digital Network). Heavily used topologies today are SD-WAN and FTTH (Fiber To The Home).