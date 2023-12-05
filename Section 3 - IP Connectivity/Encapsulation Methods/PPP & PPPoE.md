<span style="color:#f00">This is not required for the CCNA</span>
*Point-to-Point Protocol* is a [[WAN (Wide Area Network)|WAN]] oriented, data link (layer 2) protocol that encapsulates the layer 3 packet to send in a point-to-point connection between two devices.

Because it is a data link protocol, PPP replaces Ethernet. Here is the structure of a PPP frame:

![[Pasted image 20231204212144.png]]

*Point-to-Point over Ethernet* is a protocol used to carry over PPP frames inside Ethernet frames. The general strategy for this is inserting the PPP headers inside the data payload, and encapsulate it with ethernet headers and trailers.

A little quirk from this is that, because these PPPoE headers add 8 bytes to the packet data, the maximum transmission unit (MTU) and maximum segment size (MSS) have to decrease from the normal 1500 and 1460 bytes to 1492 and 1452, respectively, in order to fit inside a normal ethernet frame.