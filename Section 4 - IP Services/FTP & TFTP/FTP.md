*File Transfer Protocol* is an application layer protocol (layer 7) that provides file transference over TCP between clients and servers. FTP is more reliable and robust then [[TFTP]], providing TCP sessions alongside with other services such as file listing (get the list of files on a server) and authentication (username + password credentials).

FTP uses ports **TCP/21** (for the **control connection**, where FTP commands and authentication takes place) and **TCP/20** (for the **data connection**, where file transfers take place).

Because FTP uses different ports for commands and actual data transfer, a new TCP session needs to be established every time a transfer is needed. When this happens, two types of methods can be used:

- **FTP Active Mode**: when the server begins the new TCP session;
- **FTP Passive Mode**: when the client begins the new TCP session;

Passive mode is necessary because things like [[NGFW and IPS (Firewall)|firewalls]] and [[NAT]] can make so that outbound to inside requests are negated or lost, making it impossible for the server to start the transfer.

![[Pasted image 20231109144106.png]]

FTP also has a newer version (**FTPS** - File Transfer Protocol Secure), which transfer files over TLS for payload encryption.

Another protocol for file transfer based on FTP is **SFTP** (SSH File Transfer Protocol).