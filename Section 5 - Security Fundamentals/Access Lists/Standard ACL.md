 A *Standard Access-Control List* is a tool for controlling traffic through a switch or router, based on the source [[IPv4 Addressing|IP address]] of the packet. It can be used to drop undesired flows of traffic or to just identify traffic.

ACLs are configured from the global configuration mode. They can be a **numbered ACL** or a **named ACL**.

## Numbered Standard ACL

For a numbered standard ACL configuration, first specify a number for the ID of the ACL, then permit or deny, followed by the network source address to verify (using wildcard mask bits):

```IOS
R1(config)# access-list 1 deny 192.168.0.57 255.255.255.255
```
> Denies traffic from the 192.168.0.57/32 host

```IOS
R1(config)# access-list 1 permit 192.168.0.0 0.0.0.255
```
> Permits traffic from the 192.168.0.0/24 subnet

Then, each ACL must be applied to an interface to filter either **incoming traffic** or **outgoing traffic**:

```IOS
R1(config)# int g0/1
R1(config-if)# ip access-group 1 out
```
> Applies the numbered ACL 1 to the outgoing traffic from the `GigabitEthernet0/1` interface.

This configuration, for example, denies any traffic going out of the `GigabitEthernet0/1` interface that has a source IP address of `192.168.0.57`, while allowing other traffic from it's subnet.

> Note that all ACLs has a implicit `deny any` on the bottom meaning that, if not configured, once a ACL is applied to an interface any traffic that does not match a 'permit' rule will be dropped.

### Important Notes

- ACLs are composed of **ACEs** (Access-Control Entries). These ACEs are processed by the device in the order they were created. Once an ACE is processed, the device will take the action configured and will **not try to match any other rule**. This means that the order in which ACEs are created do matter.
- **Numbered ACLs have a range of possible IDs: 1-99 and 1300-1999. ACL IDs must be in this range for them to be valid**.

## Named Standard ACL

Although they do not differ much in functionality from numbered ACLs, named ACLs can be great when trying to organize and keep track of changed in ACL rules. To do this, first enter named ACL configuration mode:

```IOS
R1(config)# ip access-list standard MY_ACL_NAME
R1(config-std-nacl)# 
```

Then, configure rules as normal:

```IOS
R1(config-std-nacl)# deny 192.168.0.57 255.255.255.255
R1(config-std-nacl)# permit 192.168.0.0 0.0.0.255
```

And apply as such:

```IOS
R1(config)# int g0/1
R1(config-if)# ip access-group MY_ACL_NAME out
```

## Numbered ACLs in Named Config Mode

Numbered ACLs can also be configured with the named ACL configuration mode. Using this can make it easier to create access lists, and it is also the only way to edit specific ACEs from an ACL (with the `no <entry-number>` in the ACL configuration mode). There is also the possibility to insert new ACEs between already created ones by specifying the entry-number upon creation:

```IOS
R1(config-std-nacl)# 30 deny 192.168.2.0 0.0.0.255
```

## Observations

- ACEs can be reordered inside an ACL by using the `resequence` command:
```
R1(config)# do show access-lists
Stardard IP access list 1
  1 deny 192.168.1.1
  2 deny 192.168.3.1
  3 deny 192.168.2.1
  4 deny 192.168.4.1
  5 permit any

R1(config)# ip access list resequence 1 10 10*
R1(config)# do show access-lists
Stardard IP access list 1
  10 deny 192.168.1.1
  20 deny 192.168.3.1
  30 deny 192.168.2.1
  40 deny 192.168.4.1
  50 permit any
```
\*the command is `ip access list resequence <ACL-number> <first-entry-seq-number> <increment>`.

