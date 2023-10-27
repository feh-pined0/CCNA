Although OSPF is a link state protocol (i.e. reacts to changes in topology via link states), it uses timers to maintain the neighbors relationship. The default timers are:

- **Hello**: interval used to send hello messages to neighboring OSPF routers. **10 seconds by default**;
- **Dead**: countdown timer to determine when a router is no longer neighboring another router. Resets each time a Hello message is received. **40 seconds by default**;