A hypervisor is a software that provisions computing resources to and manages multiple virtual machines on a system. Hypervisors control which virtual machine gets what amount of resources and can be of type 1 or 2.

Type 1 hypervisors, also called "bare-metal" or "native" hypervisors, run directly on top of hardware and makes available to the virtual machines it manages the resources the machine has. One example would be VMWare's vSphere (or ESXi).

Type 2 hypervisors run on top of a operational system, running on top of the hardware, in a way that there is one more abstraction layer between the virtual machine and the system's hardware. An example would be Oracle's VirtualBox.