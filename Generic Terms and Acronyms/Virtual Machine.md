A *Virtual Machine* is an emulation of another computer system contained inside a system. This emulation can take many forms (such as kernel level emulation or hardware level emulation) but the general concept for virtual machines (also called VMs) is that of a virtual hardware made available from a [[Hypervisor|hypervisor]] to the VM.

The resources for this provided virtual hardware are sourced from the host machine. Thus, a virtual machine cannot have more resources than it's host machine.

A VM can run any operational system that it's hypervisor supports. The VM's operational system is called the "guest OS", and the host's is called "host OS".