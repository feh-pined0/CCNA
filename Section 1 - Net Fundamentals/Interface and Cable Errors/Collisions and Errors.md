Collisions are an ethernet mechanism that enables endpoints to communicate over shared media. Ethernet uses [[CSMA CD and CA|CSMA/CD]] (*Carrier Sense Multiple Access / Collision Detection*) to detect collisions over the network and control the flow of data sent over the shared media. Networks using CSMA/CD have the devices "listen" to the ethernet media and send data only when the media is available and other devices are not using it. When two devices transmit frames at the same time and a collision occurs, the devices can be aware of it, stop transmitting and wait a random amount of time before trying again.

Today, most cables and interfaces offer support to full duplex communication between devices thus eliminating the need for CSMA/CD. But for half-duplex communication collisions can still occur. These collisions may have many causes, but the most commons are interface duplex/speed mismatch (when the two endpoints have different duplex and/or speed configurations) or cable integrity (when a cable is bent/bad or is not suited for the desired operation mode, i.e a cat 3 cable for GigabitEthernet).

Collisions and other types of errors can be inspected with the ``show interfaces [interface]`` command. Here is an example of that command running on a Cisco IOS Router:

```IOS
R1> show interfaces g0/0

GigabitEthernet0/0 is up, line protocol is up
  Hardware is Gt96k GE, address is c201.1d00.0000 (bia c201.1d00.0000)
  MTU 1500 bytes, BW 1000000 Kbit/sec, DLY 1000 usec,
     reliability 255/255, txload 1/255, rxload 1/255
  Encapsulation ARPA, loopback not set
  Keepalive set (10 sec)
  Full-duplex, 1000Mb/s, 1000BaseT (*1)
  ARP type: ARPA, ARP Timeout 04:00:00
  Last input never, output 00:00:02, output hang never
  Last clearing of "show interface" counters never (*2)
  Input queue: 0/75/0/0 (size/max/drops/flushes); Total output drops: 0
  Queueing strategy: fifo
  Output queue: 0/40 (size/max)
  5 minute input rate 0 bits/sec, 0 packets/sec
  5 minute output rate 0 bits/sec, 0 packets/sec
     0 packets input, 0 bytes
     Received 0 broadcasts, 0 runts, 0 giants, 0 throttles (*3)
     0 input errors, 0 CRC, 0 frame, 0 overrun, 0 ignored (*4)
     0 watchdog
     0 input packets with dribble condition detected
     2 packets output, 403 bytes, 0 underruns
     0 output errors, 0 collisions, 1 interface resets (*5)
     0 unknown protocol drops
     0 babbles, 0 late collision, 0 deferred
     0 lost carrier, 0 no carrier
     0 output buffer failures, 0 output buffers swapped out
```

Here, the most helpful lines to identify interface and cabling errors are marked with (\*n):

- **\*1**: this line show the current configuration for interface standard (*1000Base-T*), speed (*1000Mb/s*) and duplex mode (*Full-Duplex*). These also show if the interface has been manually configured for duplex and speed settings. If not, then it would display "auto" as it's configuration, alongside the negotiated speed, in case the interface line protocol is UP.
- **\*2**: this line shows how many times the interface error counters have been reset. It also show when the last clearing was executed.
- **\*3**: here we can check how many broadcasts, runts (frames smaller than the minimum required size, in bytes), giants (frames larger than the maximum size for the interface, also in bytes) and throttles the interface has received. Too many runts or giants could indicate that there is a wrong configuration on any side of the line, such as the MSS (*maximum segment size*) being manually configured.
- **\*4**: an input error is any frame that arrives at the interface with an odd/wrong data-link header data. Errors caught on this counter usually have a wrong [[CRC checksum]]. This can be caused by collisions, which usually indicate a duplex/speed mismatch configuration.
- **\*5**: this counter indicates how many frames sent by this interface had any type of error and could not arrive at the destination. Generally, this means that the CSMA/CD caught a collision with a frame sent by this interface.
