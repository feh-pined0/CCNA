With the IPv4 exhaustion, IPv6 is the long term solution for the problem. Although things like [[NAT]] and [[VLSM]] were helpful to mitigate the problem, they do not solve it completely.

IPv6 has a lot in common with [[IPv4 Addressing|IPv4]]: both are layer 3 (network/internet) addresses used in routing protocols. Both have a network prefix followed by a host identifier and both need to be interpreted in binary in order for it to make sense in configuration. The main difference between them is size of the address (in bytes): while IPv4 has 8 bytes (32 bits), IPv6 has 16 bytes (64 bits). This greatly increases the number of available addresses for allocation and thus solves our problem.

IPv6 is structured the same as IPv4: an address has a subnet mask that identifies the network and host parts of the address. IPv6 however does not use address notation subnet mask (i.g. `255.255.255.0`), but it rather uses slash notation (using the same example as before, `/24`). Also, it does not use decimal notation for representing octets, these are represented using [[Hexadecimal|hexadecimal]], as to reduce the displayed size of the address.

## Main differences between IPv4 and IPv6

- IPv6 has 64 bits. IPv4 has only 32 bits;
- IPv6 uses only slash notation subnet mask. IPv4 uses both (slash and address notation);
- IPv6 octets are represented using hexadecimal; IPv4 uses decimal;

An IPv6 consists of 64 bits represented as 8 groups of 4 bytes separated by two dots (*:*). So, an IPv6 would look something like this: `2001:0db8:3333:4444:5555:6666:7777:8888/64`, where `2001:0db8:3333:4444` would be the network prefix and `:5555:6666:7777:8888` would be the host identifier.

## Identifying IPv6 network prefixes

When working with IPv6 network prefixes and mask, if we have a mask that is a multiple of four, it is easy to identify the network part of the address, since each hexadecimal digit is four bits:

`2001:0db8:3333:4444:5555:6666:7777:8888/64` - $64/4=16$ digits of the address represent the network prefix, so it's `2001:0db8:3333:4444`.

If it is not a multiple of four, a conversion is needed to identify which bits belong to the mask, and which belong to the host identifier. An example would be:

`2001:0DB8:0000:FEED:0DAD:018F:6001:0DA3/62` - $62/4=15,5$. Here, hexadecimal digits 1 through 15 belong to the netmask, and part of digit 16 also takes part in this mask. As each hexadecimal digit is 4 bits, $62-(15*4)=2$ bits of the 16th hexadecimal digit belong to the mask.

To identify the network prefix, it is needed to first set all bits to 0 unless it makes part of the mask, in which case it does not change. So, `2001:0DB8:0000:FEE` do not change. `D` is divided: part of it (2 bits) belong to the netmask, and 2 bits belong to host identifier. [[Number Notation Prefix|0xD]] = [[Number Notation Prefix|0b1101]], so bits $11$ belong to the netmask and cannot be changed. Bits $01$ belong to the host and should be set to 0, so this byte should be 0b1100, which is 0xC.

Finally, the byte `D` gets replaced with the hex `C` that was calculated, and the result is the network prefix: `2001:0DB8:0000:FEEC::/62`.

[This video](https://www.youtube.com/watch?v=ZNuXyOXae5U) covers more examples on this.