A *Broadcast Domain* is a group of devices that will receive a broadcast frame (that it, a ethernet frame with a destination MAC address of `FFFF.FFFF.FFFF`) sent by any member of the domain.

The following image has four broadcast domains:

![[Pasted image 20230828203112.png]]

Generally, only layer 2 devices forward broadcast frames. So a switch will forward this frame but a router will not. Also, it is possible to forward broadcast frames over layer 3 networking (see [[VXLAN]]).

