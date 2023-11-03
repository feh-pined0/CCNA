NTP servers and clients can configure authentication to ensure that only clients and servers with the same **authentication key** will synchronize their clocks.

To do that:

- Configure NTP authentication on all intended devices with `ntp authenticate` command;
- Configure an NTP key with the `ntp authentication-key 1 md5 <key>` command on all devices;
- Configure the trust on this key with the `ntp trusted-key 1` command;
- On all devices except the [[Useful NTP Commands|master server]], configure the NTP server and peers normally, but also include the key on the command
	- For example, `ntp server 10.0.12.1 key 1`. This will make the client attempt to authenticate with the selected NTP server.