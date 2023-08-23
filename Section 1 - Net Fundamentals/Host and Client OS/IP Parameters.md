To verify network parameters on client OSs there are generally two options:
- Using the GUI (*Graphic User Interface*);
- Using a terminal emulator;

How it is done depends on the underlying operational system.

## Windows

Depending on the Windows version in use, the GUI approach can differ, but generally, network settings can be found under the "Start" menu, then "Settings" > "Network & Internet" > "Status". Here Windows displays information such as the IP address of the selected interface, hardware description such as interface hardware and MAC address, default gateway and DNS servers.

![[Pasted image 20230816202942.png]]

For the CLI approach, Windows have two major programs two verify and configure IP parameters: `ipconfig` and `netstat`. The first one, when administered in the command line, displays information about the active NIC (*Network Interface Card*) and, when combined with the `/all` option, also display information about all other NICs on the computer (physical or virtual, on or off). The second one can display information about connectivity, such as listening [[TCP and UDP]] ports and routing table entries.


![[Pasted image 20230816203123.png]]
## MacOS

MacOS's GUI network settings can be found under "System Preferences" > "Network". It displays about the same level of information that Windows does in it's GUI. Note that "Router" here is the default gateway for this interface (Ethernet).

![[Pasted image 20230816203741.png]]

The CLI option for MacOS is `ifconfig` (as in, "interface configuration" > "ifconfig"). It displays information about the interfaces and their IP configurations, but do not show information about default gateways or DNS servers. Rather they are displayed when issuing the command `netstat`.

![[Pasted image 20230816205110.png]]

![[Pasted image 20230816205131.png]]

## Linux

Defining a way to configure and verify IP parameters in Linux can be hard. This is because today Linux has a long list of operational systems, and with each OS, things can change when it comes to settings.

A lot of distributions will have a GUI to verify network configurations. They are generally found under "Settings" > "Network". Examples will use Ubuntu 22.04 LTS (*Long Time Support*).

![[Pasted image 20230816210717.png]]

For CLI, Linux generally have the `ifconfig` also, but that is gradually being substituted for the `ip address show` command, which have a very similar output. In Ubuntu 22.04, Linux also have the network manager CLI command `nmcli`, which provides many tools for network configuration on the CLI, including device inspection with the `nmcli device show [dev]` command.

![[Pasted image 20230816211049.png]]

![[Pasted image 20230816211124.png]]