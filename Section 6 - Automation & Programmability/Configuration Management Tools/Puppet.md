*Puppet* is a [[Management Tools Overview|configuration management tool application]] that aims to facilitate the management of a large group of devices.

Puppet is *agent-based*. This means that Puppet needs software to execute on the devices it aims to manage in order for it to work. Although it is possible to run Puppet in a "compatibility mode" but putting a proxy that uses SSH in front of the target device, then this proxy would communicate with Puppet for the managed device.

Puppet uses different files for defining configurations for devices:

- **Manifest Files**: written in proprietary language, this file defines the "desired configuration state of a network device";
- **Template Files**: written in proprietary language, defines temples for the creation of manifest files;

The Puppet server is called a **Puppet Master**. It listens on port **TCP/8140** for devices looking to update/upgrade their configurations from the server (in a client-server pull style).

Puppet uses [[REST APIs]] to communicate between agents and server, or proxy and server.

![[Pasted image 20231125150305.png]]

