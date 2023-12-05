When individual devices need to access resources on a private network, they need first to connect to said network. This is usually done with a [[VPN]] tunnel using any VPN client software (such as **Cisco AnyConnect**).

The process is generally as follows:

1. Any device will [[AAA|authenticate]] with a VPN server on the network they wish to access resources from. This authentication can take many shapes and forms;
2. Once authenticated, a VPN tunnel will form between the specific device and the VPN server;
3. The device's tunnel virtual interface will behave like an interface connected to the private network;

![[Client VPN Tunnel.png]]

