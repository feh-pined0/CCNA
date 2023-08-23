The *Cyclic Redundancy Check* is a error detecting method for verifying digital data. It works by calculating a *short check value* from the input data and appending it to the data itself. Then later this value is calculated again and compared to the check value (often called **checksum**). If the values do not match, the original data is considered to be altered or corrupted in some form.

CRC is applied in some storage devices (like consumer RAM memory, for example) and vastly on networks (ethernet and 802.11 layer 2 frames). The latter has a dedicated field and algorithm to calculate this CRC: the FCS (*Frame Sequence Check*).

FCS is calculated for every ethernet frame that a device sends out. This includes wired and wireless devices.