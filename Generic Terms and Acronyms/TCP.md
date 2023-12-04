The *Transmission Control Protocol* (TCP) is one of the layer 4 (transport layer) protocols. It provides various services, the main one being host-to-host data exchange and communication. This means that TCP encapsulates data from the application layer and uses the lower three layers (internet, data-link and physical) to deliver segments. To provide this host-to-host communication it uses sessions.

TCP is a connection oriented protocol. This means that it will attempt to establish a session with the target host before sending any application data over the network. The way it does it is by using the [[Three-way Handshake|three-way handshake]].

![[TCP_Header.png]]

TCP offers some services to the application using it, including flow control (using the Window Size bytes, hosts using TCP can agree on how many segments can be sent before an endpoint need to acknowledge these segments, thus increasing or reducing the data flow), data integrity (using the Checksum bytes, hosts can verify if the segment has been altered during travel), arrival assurance (if an ACK segment is not received when it is due, a host will re-transmit the segment(s)), data sequencing (TCP can re-order segments that arrived out-of-order before sending the segment to the upper layers), and other useful services.

All these features make TCP stand out as a reliable protocol. But it also makes it so that TCP can be a little slower then other, connection-less protocols, such as [[UDP]].