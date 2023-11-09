*Trivial File Transfer Protocol* is an application layer (layer 7) protocol that provides simple file transfers between a client and server. It differs from [[FTP]] in the sense that it provides **only the file transfer** (it does not have security, encryption, session or commands). A client will request a file, and a server will provide, if it has that file.

TFTP uses port **UDP/69**. Because of this, TFTP does not have the benefits of a TCP session (ie. data delivery guarantee), but it implements acknowledgements into the protocol itself.

TFTP provides a "connection" between peers using the following structure:

- The client sends a **file request** to the server;
	- This is sent to UDP/69;
- The server responds with the first **data block**;
	- Here, the server generates a random ephemeral port;
	- The communication between server and client will now use just the two randomly generated ephemeral ports in this process (together they are called the **TID** - Transfer ID);
	- This part of the process is considered the "connection" between peers;
- The client sends an acknowledge (ACK);
	- If the client does not send an ACK, the server will not send the next data block;
	- After some time, if the client does not receive the next data block, it will assume the previous ACK did not arrive and will send another one;

![[Pasted image 20231109142851.png]]

