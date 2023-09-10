This feature allows for a bridge to automatically move from a blocking state to a forwarding state immediately, if it receives a BPDU that is inferior than the one it is receiving in its root port.

Refer to this example:

![[Pasted image 20230910173604.png]]

Here, SW2 lost connectivity to SW1 (the root bridge). It then assumes it is the root bridge (because it does not receive any more BPDUs) and starts sending its own BPDUs.

SW3 receives BPDUs on the root and non-designated ports. Normally, it would drop the inferior BPDUs received on the non-designated port until its [[Timers|max age timer]] expired, and then move to a listening, then learning state and finally a forwarding state.

With BackboneFast enabled, SW3 would make this transition immediately upon receiving SW2's inferior BPDU.