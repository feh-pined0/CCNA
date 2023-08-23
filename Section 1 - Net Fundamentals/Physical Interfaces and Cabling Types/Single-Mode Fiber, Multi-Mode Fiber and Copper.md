Connecting [[Endpoints|endpoints]] at layer 1 is one of the most important parts of networking. Not only networking would not be possible without it, but when defining aspects such as bandwidth and latency requirements for the network segment and topology, there is a lot to decide on the type of media that will be used.

Types of media, on the surface, can be separated in wired and wireless media. When using wired, there is a lot of options for a lot of cases, such as coaxial, copper, fiber, etc.

### Copper Media

Copper media is the most common between them. It's used to connect devices to each other inside the LAN (these are not used on any type of WAN topologies). These types of cables had many iterations over the past that improved performance. They consist of twisted pairs of copper cables (usually four pairs) that transmit the ethernet frames over electrical signals. Some characteristics are:

- **Cheap and available**: copper media cables are by far the cheapest and most available networking media;
- **Easily made**: copper media cables can be manually made by hand. No need for high precision machines;
- **EMI**: copper cables are twisted to try to minimize electro-magnetic interference, which can cause frames to be lost and re-transmitted.

Copper media standards are the following:

|   Standard   |   Speed   |   Cable   |
| ------------ | --------- | -------- |
| 10BASE-T     | 10Mbps      | Cat3  |
| 100BASE-TX | 100Mbps   | Cat5  |
| 1000BASE-T | 1000Mbps | Cat5  |
| 2.5GBASE-T | 2500Mbps | Cat5e|
| 5GBASE-T    | 5000Mbps | Cat6   |

There are more standards than this, but these are the most commonly used.

### Fiber (Multi and Mono Mode)

Fiber is a relatively new type of media that is arriving at the consumer through topologies such as FTTH or FTTP. In contrast to copper, fiber cables use a type of glass or plastic as it's transfer media and do so by transmitting signals through light. This light is usually a laser (in the case of single mode fiber) or an LED (for multi-mode fiber, although this one can also use laser). These cables consist of a core of glass or plastic, encapsulated by a cradling to avoid the light from "escaping" the core and encapsulated yet again for protection.

For multi-mode fiber, the core can take a diameter of up to 50 microns. It's called "multi-mode" because light bounces inside the core, reflecting through the path in many modes to arrive at the other endpoint. Because of this, multi-mode fiber has less speed and higher attenuation than single mode fiber.

![[Pasted image 20230724173048.png]]

Single mode fiber's core is no wider than 9 microns, and can be as wide as 5 microns. This is because in this cable the light must traverse through the path in only one mode. This means that the light does not bounce inside the core and travel in a straight line across it, making it much faster and reducing attenuation.

For single mode fiber, the speed standards are the following:

|      Standard    |     Speed    | Distance | Wavelength |
| -------------- | ----------- | --------- | -----------  |
| 1000Base-LX | 1000Mbps  |    5Km     |     1310nm   |
| 10GBase-LX4 |    10Gbps   |    10Km    |     1310nm   |
| 10GBase-E     |    10Gbps   |    40Km    |     1550nm   |
| 40GBase-LR4 |    40Gbps   |    10Km    |     1310nm   |
| 40GBase-FR |    40Gbps   |    2Km    |     1310nm   |
| 100GBase-LR4 |    100Gbps   |    10Km    |     1310nm   |

For multi-mode fiber, the speeds and distances depends on the cable grade, as described in this table:

![[Pasted image 20230724181009.png]]