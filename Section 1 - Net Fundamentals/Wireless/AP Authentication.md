Before sending any data to the network through an AP, a client needs to perform the association process, in order to associate with the [[Access Points|access point]]. This needs six steps:

- **Probe request**: the client broadcasts a probe request to check for available [[Service Sets|BSSs]] in the wireless media;
- **Probe response**: the APs send a probe response with information about it's advertised BSSs;
- **Authentication request**: the client sends a authentication request with the needed parameters for authenticating into the network;
- **Authentication response**: the AP responds with the authentication transaction status (failed or successful);
- **Association request**: the client, now authenticated, requests for association with the AP.
- **Association response**: the AP responds with the association status.