NAT can perform dynamic address translations. This ensures that configuring NAT for multiple addresses can be done in a non-exhaustive way. Also, dynamic translations allow for multiple private addresses to be mapped to a single public IP.

Dynamic NAT works by configuring an [[ACL]] that describes which IPs should be translated, defining a pool of available inside global addresses and activating inside source translation.

> Note that, while ACLs are used to define which IPs should or shouldn't be translated, a packet whose source IP does not match the ACL **will not be dropped**. The IP will simply not be translated. The packet will **only be dropped in case the inside global IP pool is exhausted**, in which case the router will not have any inside global IP to assign to the packet.

Dynamic translations will create dynamic entries in the `show ip nat translations` table. New dynamic translation entries expire **24 hours after their creation**. Protocol address translations expire around 1 minute after the creation.