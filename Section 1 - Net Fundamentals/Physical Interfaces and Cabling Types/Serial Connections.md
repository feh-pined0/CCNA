<span style="color:#fcba03;">Not so relevant to CCNA anymore, but interesting for practical Boson labs</span>

*Serial Connections* are no longer used so much today, because fiber, alongside with ethernet, has dominated the market because of faster speeds and great reliability.

Serial media has a different set of packet encapsulation data link protocols in order to operate. These connections use serial cables that have two different endings: a **DTE** (*Data Terminal Equipment*) and a **DCE** (*Data Circuit-Terminating Equipment*). The device connected to the DCE side of the cable should have additional configuration to set things like the clock rate for both devices.

![[Serial Connections.png]]

## Serial Sub-interfaces

Serial interfaces also support sub-interfaces. This is used to facilitate point-to-multipoint connections using protocols like frame-relay.