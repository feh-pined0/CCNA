Telnet and SSH (*Secure Shell*) are two methods for establishing a remote connection to a network device (or any device that supports a terminal).

Both methods work by opening a [[Terminal Emulators|terminal emulator]] to simulate a serial connection to the device over a network. SSH uses ports [[TCP]]/22 and Telnet uses port TCP/23.

Telnet and SSH differ by their security. While Telnet sends clear text data over the ethernet media, SSH encrypts the data sent using [[Encryption|asymmetric key]]. The connection can be made verifying only the server (the server holds the public and private key) or verifying the server and client (in the case the client's private key is shared with the server).

A connection to a network device using SSH or Telnet can be made using a popular software called PuTTY:

- Install and open the PuTTY terminal emulator;
- Connect the computer to the network device through ethernet or wireless media;
- Select the "SSH" or "Other" method for connecting the device;
- Type in the device's IP address;
- Click "Open";

![[Linux Virtual Teletype Configuration 2.png]]