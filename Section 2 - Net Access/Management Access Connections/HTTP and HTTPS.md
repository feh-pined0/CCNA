Remote management through HTTP and HTTPS are becoming more common on modern days. Usually, network configuration through web interfaces were only common when handling [[Controllers (WLC & Cisco DNA Center)|wireless network devices]].

Configuration of network devices using HTTP nowadays is much more common and preferred. This is because it is much more simple to configure using a graphical interface. Also, these interfaces help visualize data in a manner that the CLI just could not, which is a plus for automation.

## Configuring a device

To configure a device through HTTP or HTTPS, a web browser is opened on a client and the [[IPv4 Addressing|IP address]] of the device is searched (HTTP uses port TCP/80 and HTTPS uses TCP/443). A web portal is then presented, usually requiring login credentials. After that, configurations can be applied using a graphical interface.

> Example of a configuration GUI from a network device:
> ![[Cisco Device HTTP Management.png]]

