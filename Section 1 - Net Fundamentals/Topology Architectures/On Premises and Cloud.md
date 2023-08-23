Clouds and on-premises are two kinds of topologies that complement one another. These describe where on the network will the computing resources be made available. Traditional IT topologies had two ways for using computing resources for their business:

- **On Premises (On-Prem)**: equipment such as servers and networking devices would be available on-site for the company. This means that the company would buy and own the equipment it uses, and it would be located at one of the company's offices or data centers. This requires a lot of [[CapEx]] and capable professionals to handle the equipment.
- **Co-location**: in this instance, equipment would be located by a third-party for a company. The company in question usually does not own the equipment, but is responsible for managing and using these resources. The third-party locating the equipment takes care of physically maintaining and securing the devices.

Companies usually had one or some combination of these two.

Cloud topology is a fairly "new" concept (the [NIST document](https://nvlpubs.nist.gov/nistpubs/legacy/sp/nistspecialpublication800-145.pdf) describing cloud services dates from 2011), it has **five** main, essential characteristics that should be accomplished when providing such services.

## Five main characteristics of cloud services:
- **On-Demand Self-Service**: the client should be able appropriate the resource it wants through a automated process (usually a web portal) with minimal interaction with the service provider.
- **Network Broad Access**: the access to these resources must be made available over the network and managing these resources must be possible using heterogeneous clients, such as desktops and mobile phones (again, usually through a web portal or web-app).
- **Resource Pooling**: the resources available to the costumer must be pooled in some way that it appears to be infinite to the client. The client should be able to appropriate these resources without needing to know the exact location of the servers that are pooling it.
- **Rapid Elasticity**: The costumer must be able to expand or shrink the use of cloud resources in an easy, fast way. This process can be manual or automatic. An example would be allocating more RAM or storage volumes on a existing server because of business demand increase.
- **Measured Service**: the services provided must have a way to be measured by the service provider and costumer. From these measures, the provider and the costumer can calculate costs for allocating these resources in a transparent way for both (for example, defining a X cost for using a vCPU for a day).

Cloud service providers can deliver these services using three main models (there are more models, but these three are the essential ones). These models describe the "access level" of the costumer over the resources they are allocating.

## Three cloud service models:
- **Software as a Service (SaaS)**: in this model the service provider makes the whole software available through the network, from the infrastructure needed to run the software to the software itself. The costumer usually pays a fee to have access to this software (hence the name). One example would be Google's G-Suite, which provides a office suite of tools such as Google Docs and Google sheets.
- **Platform as a Service (PaaS)**: here the entire platform is provided to the costumer for them to build or deploy their software as they see fit. The service provider does not make available the final software or app product but rather provide the platform that the costumer app needs to run. The client does not have control over the infrastructure or the tools available, and has control only over which software will this platform run. One example would be Google Apps Service or Google Scripts, which run on Google's platforms, but the script or app itself is provided by the costumer.
- **Infrastructure as a Service (IaaS)**: lastly, in IaaS the costumer has the most control over the environment. The service provider only makes available a pool of resources to the client, which in turn appropriates these resources as they see fit. In this case, the costumer can choose the amount of resources it needs, the devices (such as [[Servers|servers]], [[Routers|routers]], [[NGFW and IPS (Firewall)|firewalls]], etc)

Finally, these topologies can be deployed using three deployment models that dictate the "level of ownership" of the cloud infrastructure.

## Three deployment models:
- **Private Cloud**: the cloud infrastructure is available only to a single company. The infrastructure does not need to be owned by the company (the provider can be a third-party), but only this company can use these resources. **May exist on or off premises**.
- **Community Cloud**: the cloud infrastructure is share among companies that share common interests. It is only available to this community and no one else. The cloud provider can be one of the companies of the community or a third-party. **May exist on or off premises**.
- **Public Cloud**: the cloud infrastructure is made public available for the general consumers. It may be made available by a business, government or community and **it exists on the premise of the provider**.
- **Hybrid Cloud**: it is any combinations of private, community or public clouds that "...remain unique entities, but are bound together by standardized or proprietary technology that enables data and application portability".

To provide this elasticity to the service, providers and clouds use [[Virtual Machine|virtual machines]], allowing these resources to be pooled. Virtual machines run on top of [[Hypervisor|hypervisors]], generally a type 1 hypervisor.

It is good to remember that, while on-premises and cloud services appear to be opposites, they actually complement each other. Cloud services can be provided on premises to costumers that may or may not be the same company.