*Ansible* is a [[Management Tools Overview|configuration management tool application]] that aims to facilitate the management of a large group of devices and device classes.

Ansible is *agentless*. This means that **it does not require software to be installed in the devices that are going to be managed**. This makes Ansible very versatile as it can configure any device that supports [[Telnet and SSH|SSH]].

Ansible works by defining a set of:

- **Inventory Files**: files written in YAML that define a set of devices that can be managed, as well as their characteristics;
- **Template Files**: files written in YAML that define configuration templates for devices;
- **Variable Files**: files written in Jinja2 that define a configuration pattern to apply in a template for a specific configuration;
- **Playbook Files**: files written in YAML that define a course of action to apply a configuration based on the three types of files above (so a template, inventory and variable files are used to apply a configuration);

As Ansible uses SSH, it's used port for managing devices is **TCP/22**.

![[Pasted image 20231125145204.png]]

