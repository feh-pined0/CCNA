Servers are generally associated with high availability, powerful machines that can run mission-critical applications. When deploying a server, however, much of these resources can be underutilized (if the deploy of applications is done correctly. i.e. not deploying multiple applications on the same server). This is because in order to have a good application architecture, it is a **must** to deploy different applications on different servers.

Buying and deploying a server is **expensive**: not only does the hardware cost far more than the average consumer PC, but it is also needed experience and knowledge to configure these systems.

For these reasons, virtualization is a core function of all data centers. By virtualizing multiple servers in one hardware, the resources can be more accurately allocated, data can be encapsulated, and applications can reside in a more controlled ambient.

Virtualization can occur in various forms:

- Type 1 Hypervisor Virtualization: in this case, a [[Hypervisor|hypervisor]] is installed on top of the bare hardware, and [[Virtual Machine|VMs]] are configured on top of the hypervisor;
- Type 2 Hypervisor Virtualization: this is more common to use with non mission-critical applications. Here, the hypervisor is installed on top of a OS that is already on top of the bare hardware;
- [[Containers]]: this is a special type. Containers are a OS-level virtualization, meaning that only the OS is virtual, as opposed to other VMs that virtualize hardware and kernel too. This means that containers are far more compact and portable than VMs. The basic premise for container operation is that, instead of virtualizing the entire OS, the container uses the host OS to make system calls, and virtualize only trivial stuff such as file system and networking.

![[VMs & Containers.png]]