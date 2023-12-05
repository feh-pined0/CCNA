In order for QoS to correctly prioritize traffic, a classification process must take place. This classification process happens on forwarding devices such as switches (layer 2) and routers (layer 3) and many **parameters are taken into account** when classifying traffic:

- **Access-Lists**: ACLs can be used to manually determine which traffic should be prioritized or not. In this case, the ACL will be used just to identify traffic, not to drop it (although if QoS may drop packets of low priority);
- **NBAR** (Network Based Application Recognition): it is a mechanism that performs **deep packet inspection** in order to determine traffic class. It can inspect information of up to layer 7 of a PDU, identifying which ones should be prioritized based on the application being used (for example, HTTP traffic may be low priority, while HTTPS is prefered);
- **PCP** (Priority Code Point): is a field of the [[802.1Q Header|802.1q tag]] for the ethernet frame. It has 3 bits with 8 possible values. The higher the value, the higher the priority. It is defined in the IEEE 802.1p standard.
	- Can only be used when a frame is 802.1q tagged.
	- Also called **CoS** (Class of Service)
- **DSCP** (Differentiated Services Code Point): is a field of the IP header that can be used to identify high/low priority traffic;

## Priority Code Point

The following values are defined for PCP:

| **PCP Value** | **Traffic Class**         |
|-----------|-----------------------|
| 0         | Best effort (default) |
| 1         | Background            |
| 2         | Excellent effort      |
| 3         | Critical Applications |
| 4         | Vídeo                 |
| 5         | Voice                 |
| 6         | Internetwork control  |
| 7         | Network control       |

## Type of Service (ToS)

Bits $8$ through $15$ of the IP(v4) header are used for a **type of service** value in order to classify traffic flows. This ToS byte is further divided into two fields:

- **DSCP** (Differentiated Services Code Point): using 6 bits, there are a total of 64 values for the DSCP field;
- **ECN**: these are 3 bits that are mostly unused and not relevant for the CCNA;

DSCP values are standardized and should be configured in one of the following categories:

- **Default Forwarding** (`0d0`): this is the default value. Traffic that is not prioritized.
- **Expedited Forwarding** (`0d46`): this defines traffic that require low loss/latency/jitter such as voice and video;
- **Assured Forwarding**: AF does not have a specific DSCP value, as it represents a set of values.
	- AF is represented by `AFXY` where `X` (3 bits) is the traffic class and `Y` (2 bits) is the drop precedence;
	- The least significant bit of an AF DSCP value is always 0;
	- traffic from the same class have the same priority;
	- Drop precedence defines how likely it is for the packet to drop, in the case of congestion;
	- There are 4 traffic classes in total (`0b001`,`0b010`,`0b011` and `0b100`);
>Example of AF value:
>![[QoS DSCP Calculation.png]]

- **Class Selector**: also does not have a defined value, this class is a backward compatibility tool. Only the 3 most significant bits are used. Values range from 0 to 8 (similar to PCP);

