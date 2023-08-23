IPv4 addresses were the first kind of network addresses distributed for public use. At the time it was created, the internet was not as big as it is today, as in there was not so many devices that connect to the internet. So, as networks got bigger, network addresses started to run out.

IPv4 addresses consists of four bytes or four octets (8 bits). If we calculate that, we get $2^{32}$ IP addresses, which seems like a lot, but it is actually not that much. By 1996, IPv4 addresses already were found to be scarce. To remedy that, [RFC 1918](https://datatracker.ietf.org/doc/html/rfc1918) defined private IPv4 address ranges.

There are three (classful) private IPv4 address ranges (one for each class):

- Network 10 (10.0.0.0/8 | 255.0.0.0) class A;
- Network 172.16 (172.16.0.0/12 | 255.240.0.0) class B;
- Network 192.168 (192.168.0.0/16 | 255.255.0.0) class C;

These IP ranges are not routable on the public internet and should not be assigned to global interfaces.

Using these IPs to address private devices solves most of IPv4's problems, but it creates some others. While private networks can use the same private IPv4 ranges that other networks, because they are not routable on the public internet, they can not possibly talk to each other. Because of this, [[NAT]] was invented.