IP addresses are a type of address that is used in layer 3 (the internet/network layer). It stands for *Internet Protocol Version 4* and it's the most common type of network address. It is composed of four octets (or four bytes) and a subnet mask. Each octet can go up to 255 (decimal) for a total number of $2^{32}$ available IP addresses.

An IPv4 address has two parts: the subnet identifier and the host identifier. These can be calculated using the subnet mask of the address. A subnet mask is also composed of four octets and it indicates which bits of the address identifies the network, and which identifies the end host. So for example:

An IPv4 address of `192.168.1.57` with a subnet mask of `255.255.255.0` has the first three octets as its network (`192.168.1`) and the last octet as it's host identifier (`.57`).

IPv4 addresses can be separated by classes:

- Class A addresses have the [[MSB]] set to `0`. So, class A addresses can go from `00000001.00000000.00000000.00000000` to `01111111.00000000.00000000.00000000` or `1.0.0.0` to `127.0.0.0`. Addresses in class A have a subnet of `255.0.0.0.`

- Class B addresses have the MSB set to `1`. So, class B addresses can go from `10000000.00000000.00000000.00000000` to `10111111.00000000.00000000.00000000` or `128.0.0.0` to `191.0.0.0`. Addresses in class B have a subnet of `255.255.0.0`.

- Class C addresses have the MSBs set to `11`. So, class C addresses can go from `11000000.00000000.00000000.00000000` to `11011111.00000000.00000000.00000000` or `192.0.0.0` to `223.0.0.0`. Addresses in class C have a subnet of `255.255.255.0`.

- Class D addresses have the MSBs set to `111`. So, class D addresses can go from `11100000.00000000.00000000.00000000` to `11101111.00000000.00000000.00000000` or `224.0.0.0` to `239.0.0.0`. These addresses are used for multicasting.

Addressing hosts like this is called classful subnetting.

It is also worth noting that you cannot have subnet masks with MSBs alternating 1s and 0s. For example, you cannot have a subnet mask of `175.0.0.0` because the binary notation for that is `10101111.00000000.00000000.00000000`. So, the possible values for octets in a subnet mask is:

- 255 - `11111111`
- 254 - `11111110`
- 252 - `11111100`
- 248 - `11111000`
- 240 - `11110000`
- 224 - `11100000`
- 192 - `11000000`
- 128 - `10000000`
- 0 - `00000000`

When subnetting a network, it is essential that the number of hosts and networks is well defined. If there is going to be lots of hosts but few LANs or WANs, maybe a smaller subnet mask is better. If there are lots of network divisions, however, it may be better to allocate subnets with a larger mask.

Also, networks do not need to start exactly at 0 on a octet. For example, `11111111.11100000.00000000.00000000` is a completely valid subnet mask. It describes a network with a mask `255.224.0.0`. Networks with this mask can go from `1.0.0.0/11` to `255.224.0.0/11`. Each of these networks would have a starting IP address of (taking the network `10.32.0.0/11` as an example) `10.32.0.1` and an ending IP of `10.63.255.254`.

In this example, the network `10.32.0.0/11` described in binary, would be `00001010.00100000.00000000.00000000`. It is known by the subnet mask that the first 11 bits represent the network address so the first octet, in decimal, is 10 (`00001010`) and the second is 32 (`00100000`), but from these last 8 bits, only the last 3 can represent a network. Because of this, contrary to the immediate thought that the next network address would be `10.33.0.0/11` it would actually be `10.64.0.0/11`, because then the second octet would change the bits that actually represent the network address `00001010.01000000.00000000.00000000`, and not the end host addresses.