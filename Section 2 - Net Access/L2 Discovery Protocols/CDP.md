*Cisco Discovery Protocol* is a layer 2 [[Discovery Protocols|discovery protocol]] created by Cisco. It was the first discovery protocol created, followed by the industry standard IEEE 802.1AB (LLDP).

CDP has some advantages over LLDP. Because it is proprietary, CDP enabled devices can share more specific information about themselves, such as enabled protocols on the device.

CDP is enabled by default on every Cisco device. It operates by sending a CDP message every 60 seconds (1 minute). When a device receives a CDP message, it stores information about the sender of the message on the **CDP table**, which can be accessed using the `show cdp ...` commands.

**CDP messages are sent to the MAC address** `0100.0CCC.CCCC`.

Entries on the CDP table are stored up to 180 seconds (3 minutes) by default, and then are discarded, as the device can no longer be a neighbor.

CDP messages are not forwarded and are discarded by the receiving end no matter what. This ensures that the device only holds information about neighbors.

Here is an example of the `show cdp neighbors` command output:

![[Pasted image 20230831152711.png]]

