Applications that are sensitive to the stability of [[Network Resources|network parameters]] (such as voice and video streaming) can greatly benefit from QoS. Also, they generally have built in mechanisms that help stabilize the connection. For example, IP phones usually have a "jitter buffer", in which they buffer packets locally before using them in order to provide a more stable voice experience.

Recommended standards for interactive audio (based on the network parameters) are:

- **One-way delay**: 150 ms or less;
- **Jitter**: 30 ms or less;
- **Loss**: 1% or less;