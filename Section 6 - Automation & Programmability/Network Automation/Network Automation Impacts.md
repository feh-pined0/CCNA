When configuring and managing network and network devices, professionals often tend to manually configure devices for them to integrate and converge in the desired network topology. Traditionally, this configuration was done entirely by hand, on the CLI (using connections like [[SSH]] and [[Console]]), which is not very modern by today's standards.

Although sometimes it can be necessary to manually set up a device or parameter, groups of **many devices can be set up and configured using automation and programming strategies**.

There are many aspects of networking and network management that can be automated, and this has many benefits:

- Automated tasks in networking are less prone to human error, as when configuring many devices, a person is more likely to introduce a typo in a device's configuration;
- Repetitive tasks that are automated can reduce the time that engineers spend on them, causing them to focus on more important matters;
- It is easier to have a homogeneous policy and configuration standard if those configurations are managed by a centralized controller;

Automation can be implemented in various aspects of networking. Newer devices have APIs that allow them to communicate with many other devices, scripts can be created to automate simple tasks, etc.

> Python script to configure multiple routers at once.
> ![[Network Automation With Scripts.png]]

