A *container* is a bundle that contains:

- An app (a software or application);
- All dependencies to run this app;

This container is then instantiated (via virtualization) with a container runtime, provided by a container engine (like [Docker Engine](https://www.docker.com/) for example).

A container may seem like any [[Virtual Machine|virtual machine]] at first, but they are different in the way they operate. Although both virtualize an environment in which an app runs on top of, a virtual machine will virtualize the hardware, kernel and OS for the virtual system, whereas a container will virtualize only the file system and the OS, meaning that any calls to the system kernel are made directly to the host OS.

This makes so that containers are much smaller and portable than full blown VMs, but also are less isolated, because all containers share the same kernel and container engine.