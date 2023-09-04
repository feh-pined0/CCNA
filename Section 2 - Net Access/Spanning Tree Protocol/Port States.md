[[Classic STP]] has different port states that define what an interface can/cannot do in the network topology. There are four states in total:

- **Blocking**: A blocking interface **does not** forward ethernet frames, **does not** [[MAC Learning and Aging|add MAC address table entries]], and **does not** forward BPDUs (it only receives/listen to them). This is considered a **stable** state.
- **Listening**: A listening interface **does not** forward ethernet frames, **does not** add MAC address table entries, but they do **receive and forward** BPDUs. This is considered a **transitional** state.
	- Blocking ports do not enter the Listening state. Only designated or root ports do.
	- Also, remember that changes in topology can change which ports are blocking or designated/root ports.
- **Learning**: A learning interface **does not** forward ethernet frames, but it **does** add MAC address table entries and **receive and forward** BPDUs. This is considered a **transitional** state.
	- This ensures that, when the port begins forwarding normal traffic, it does know some of the network's MAC addresses before hand.
- **Forwarding**: A forwarding interface operates like a normal switchport. It sends and receives normal traffic as well as BPDUs. This is considered a **stable** state.