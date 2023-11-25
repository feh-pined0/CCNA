CRUD and HTTP are closely related when talking about [[REST APIs]]. Usually HTTP is the protocol of choice when implementing such structure because it has very similar components to CRUD.

CRUD stands for *Create, Read, Update, Delete*, and it defines the four main methods of a REST API. Through these methods, an application can *create* data, *read* and *update* it's contents, and *delete* it when it is convenient.

HTTP on the other hand, have very common **HTTP Verbs**. These verbs define common operations in data exchange between client and server. The more common verbs are:

- <span style="color:#32a852;">GET</span>: to retrieve a resource on a server;
- <span style="color:#ddeb49;">POST</span>: to create a resource on the server;
- <span style="color:#498ceb;">PUT | PATCH</span>: to update a resource on the server;
- <span style="color:#eb4959;">DELETE</span>: to delete a resource on the server;

These HTTP verbs have almost a direct connection to CRUD and it's because of this that HTTP is usually the prefered protocol to implement REST APIs.

For example, here is a description for accessing a resource on the northbound API of a Cisco DNA Center application:

![[Pasted image 20231123220407.png]]

