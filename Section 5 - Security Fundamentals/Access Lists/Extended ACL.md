*Extended Access-Control Lists* can be useful when trying to match more specific traffic flows. Besides being able to match traffic based on the source IP address, they can also match based on **destination IP addresses and layer 4 ports, source layer 4 ports**, and much more (although layer 3 and 4 addresses are the more relevant ones for the CCNA).

Extended ACLs can be configured with numbered IDs or Named IDs (just like [[Standard ACL]]). **Numbered Extended ACLs range from 100-199 and 2000-2699**. When configuring with numbered extended ACLs, a number ID from this range must be used.

To configure Extended ACLs, the command is:

```IOS
R1(config-ext-nacl)# [seq-num] <permit|deny> protocol src-ip dest-ip
```

Ports can be configured after the source or destination IP address by specifying a matching pattern:

- **eq**: match the specified port;
- **neq**: match anything **but** the specified port;
- **range**: match range of ports
- **lt**: match ports that are less than the specified one;
- **gt**: match ports that are more than the specified one;

