Also known as Modified Extended Unique Identifier, this is a method for converting a 48 bit [[MAC Address]] into a 64 bit IPv6 host identifier (this is, supposing the use of an IPv6 address with a subnet mask of /64). There are 3 steps to performing this conversion:

 1. Split the interface's MAC address into two, equal parts (for this example, `1234.56|78.9ABC`);
 2. In between bits 24 and 25, place the following quartets: `FFFE`. In this example, `1234.56FF.FE78.9ABC`;
 3. Finally, flip the 7th bit of the identifier. Remember, each hexadecimal number is 4 bits long, so the seventh bit resides in 0x2. 0x2 -> 0b00**1**0. Flipping 1 results in hexadecimal 0x0. So the final identifier is `1034.56FF.FE78.9ABC`.