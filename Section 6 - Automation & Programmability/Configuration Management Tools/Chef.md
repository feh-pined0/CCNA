*Chef* is a [[Management Tools Overview|configuration management tool application]] that aims to facilitate the management of a large group of devices.

Chef is *agent-based*. This means that Chef needs software to execute on the devices it aims to manage in order for it to work

Chef uses different files for defining configurations for devices (all written in *Ruby's Domain Specific Language*):

- **Resource Files**: files that describe devices that are going to be managed. In the documentation, these are called the "Ingredients" in a recipe;
- **Recipe Files**: files that describe how tasks should be executed and performed on resources. These are basically individual tasks;
- **Cookbook Files**: files that contain a relation of multiple recipes grouped. They define multiple actions that can be taken in order to properly configure a device;
- **Run-list Files**: files that contain an ordered list of recipes that are run to configure a device;

Chef listens on **TCP/10002** for client devices to pull configurations from.

Chef uses [[REST APIs]] to communicate between server and agents.

![[CHEF Topology.png]]

