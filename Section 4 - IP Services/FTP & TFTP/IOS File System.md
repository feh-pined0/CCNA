Cisco devices (as any other network device) run a operational system to administer system resources, one of them being 2 tier memory (non volatile, mass storage memory).

These devices have many file systems, each with a different type. The most common ones are:

- **Disk**: flash type of memory meant to hold simple files such as system images and information;
- **Opaque**: is used for specific internal functions. These **are not** physical devices;
- **Nvram**: (non-volatile ram): this is where system configurations are stored;
- **Network**: these are mounted **NFS** (Network File System), such as external [[FTP]]/[[TFTP]] servers;

Generally, usage of these file system is transparent. But there are times when knowledge of the device's file system is needed (when uploading a update IOS image to the device, for example).