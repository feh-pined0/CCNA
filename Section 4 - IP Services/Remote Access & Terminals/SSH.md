*Secure SHell* is a remote access protocol created to replace [[Telnet|telnet]]. It is more robust and secure, providing strong authentication and payload encryption.

SSH has two major revisions: **v1** and **v2**. On Cisco devices, when support for both versions is present, the device says it supports **version 1.99**.

The protocol relies on cryptographic keys to provide security features. Usually, [[Asymmetric Key Pairs|asymmetric keys]] are used.

>Here is an example SSH packet capture:
>![[Pasted image 20231107161014.png]]

SSH uses port **TCP/22** for the server.

## Notes

To configure SSH on a Cisco device, an `ip domain name` must be configured. This will be the device's key name.

SSHv2 requires a key length of **at least 768 bits**.