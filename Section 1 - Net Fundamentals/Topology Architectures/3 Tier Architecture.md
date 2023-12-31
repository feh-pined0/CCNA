The 3 tier adds yet another layer to the [[2 Tier Archtecture|collapsed core model]]: the **core layer**. Originally, this was the architecture used, but the costs are very high and it is a more complex network model, so it’s used only by big companies or enterprises that need the highest availability possible.

The core layer sits above the distribution layer and it’s responsible for forwarding traffic between different distribution layers. The equipment on this layer needs to be as fast and reliable as possible, as it is the backbone of the large scale LAN/MAN and will do tons of routing. The core layer is then connected to the LAN edge routers that give access to the internet or other sites.

The difference between the core layer and the distribution layer is that the core layer gets assigned the task to route through almost all the LAN and needs to be fast and reliable. It also adds another layer of network redundancy making the whole network more available and adds scalability to the topology. The following image illustrates a 3 tier network topology:

![](https://lh3.googleusercontent.com/fctH7I6HCoRj6FvV3DSF__r8HGLyvAj7zfC3faw9YuafS4WL1gAAGdmfsV2KxJI-lk5CBAVf7mr0F1mkUZutIuCSBp0pBKrGkEJl8ZEConRyK05UhkPAtczf6l2JThDzMoB1XHq0S9Nq4yasNyTOz_o)

Again, each layer 2 switch is connected to each distribution layer switch, which in turn are connected to the core layer switches and to each other to perform [[First-Hop Redundancy|first-hop redundancy]]. The core layer switches are then connected to the internet backbone or to other core layers.