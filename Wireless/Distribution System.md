When deploying wireless networks, it must be connected to a wired network (even if it is just a modem and a router, by today's standards). From the wireless LAN perspective, this wired network is called the *Distribution System*.

In the wired network, each [[Service Sets|BSS or ESS]] is mapped to a [[VLAN]] defined by the upstream interface on the wired network device.

[[Access Points]] also have the capability to provide multiple VLANs and thus multiple SSIDs on each BSS. This is done by configuring the AP and setting a trunk on the upstream interface. Generally, when doing this, the AP will generate a new BSSID based on the MAC address of the device, and incrementing one bit for each new SSID advertised by the AP.