*Console* is the traditional method for configuring a network device. It is usually the first configuration method used when deploying a new device because, at that point, the device does not have any configuration and thus does not have any connectivity to hosts that could manage it remotely (for example, using [[HTTP and HTTPS|WebUI]] or [[SSH]]).

Almost any device has a console port built in it. The console port provides a serial connection to the device (using RS-232 or USB), allowing for communication through a [[Terminal Emulators|terminal emulator]].

A connection to a network device using a console port can be made using a popular software called PuTTY:

- Install and open the PuTTY terminal emulator;
- Connect the computer to the network device through the console port using a USB or RS-232 cable;
- Select the "Serial" method for connecting the device;
- Type in the serial port name;
- Click "Open";

![[Pasted image 20230910215915.png]]

