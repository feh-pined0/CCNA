Security on WLANs (*Wireless LANs*) is very important because the wireless signals can be accessed by any device capable of wireless connections and in range of the signal. Thus, for a station to join the WLAN, a method for [[Authentication|authentication]] and [[Encryption|encryption]] is required.

# 802.11 Authentication Methods

- **Open Authentication**: does not use any type of secret. The station sends an authentication request and the AP accepts it. It can, however, be necessary for the client to authenticate with another method once connected to the network (like public networks that require web page authentication);
- **WEP** (*Wired Equivalent Privacy*): used for both authentication and encryption. The authentication process is as follows:
	- Station sends authentication request;
	- AP sends **challenge phrase** (random number of bits);
	- The station encrypts it using a **shared key** and sends it back;
	- The AP itself encrypts the data using it's version of the shared key and compares the two encryption;
	- If they match, the authentication was successful;
	WEP uses a [shared key](https://en.wikipedia.org/wiki/Shared_secret) of 40 or 104 bits with a 24 bit [Initialization Vector](https://en.wikipedia.org/wiki/Initialization_vector) appended to it, making it 64 or 128 bits in length total. Also, WEP uses [RC4](https://en.wikipedia.org/wiki/RC4) algorithm to perform data encryption.
## 802.1x Standard

The 802.1x standard defines rules for limiting the access to the network (LAN or WLAN) until client authentication. The standard defines three entities:

- **Supplicant**: the device who requests access to the network;
- **Authenticator**: the device that provides access to the network;
- **Authentication Server** (*AS*): the device that authenticates client credentials and permits/denies access;

## EAP (Extensible Authentication Protocol)

To understand the following authentication protocols, knowledge of EAP is required. This is a authentication **framework**, which defines functions that other protocols can expand on to implement authentication methods. It operates following the 802.1x standard, so any implementation of EAP is required to have those three entities (supplicant, authenticator and authentication server).

- **LEAP** (*Lightweight EAP*): developed by Cisco, it is an improvement for WEP. In this method, both the client and server send challenge phrases to each other, in order to authenticate. The client authenticates using a username and a password, and the WEP keys used for encryption are changed frequently (this feature is called dynamic WEP keys);
![[AAA Server Wireless Auth.png]]

- **EAP-FAST** (*EAP Flexible Authentication via Secure Tunneling* \[*TLS*\]): also developed by Cisco, EAP-FAST uses TLS to establish a secure tunnel between server and client, and then provides authentication via one of it's supported flows (like MS-CHAP or OTP). To form the tunnel, a **PAC** (*Protected Access Credential*) is provided for the client (this is called *PAC Provisioning*);
![[AAA Server Wireless PAC Auth Over TLS.png]]

- **PEAP** (*Protected EAP*): this is almost the same as as EAP-FAST, but instead of using PACs to provide a TLS tunnel (with shared keys), the server uses a digital certificate to form this TLS tunnel (kinda like HTTPS). It is also developed by Cisco, in conjunction with Microsoft (the image is the same as above, changing PAC -> Digital Certificate);
- **EAP-TLS**: it is almost the same as PEAP, but instead of only the server presenting it's digital certificate, the client needs to authenticate using it's certificate too. This is by far the most secure method of authentication, but it is also the most difficult to implement. Also, because the client presents it's certificate, it does not need to authenticate once the TLS tunnel is formed.

# Encryption and Integrity

After authenticating the station, data exchanged between the client and the server **needs** to be encrypted in order to keep the connection safe in the wireless media. For this, different methods were applied.

- **TKIP** (*Temporal Key Integrity Protocol*): TKIP uses the same methods of WEP for encryption (shared key secret), but it adds more features on top of it, because WEP was considered to be very insecure (even at the beginning):
	- A [[Digital Signatures and Data Integrity|MIC]] (*Message Integrity Check*) is appended to messages in order for the peers to check for the integrity of the message;
	- A key mixing algorithm is used to generate a new key to encrypt every frame;
	- The IV length increased from 24 to 48 bits;
	- It is used in WPA1
- **CCMP** (*Counter/CBC-MAC Protocol*): the *Counter Cipher Block Chaining Message Authentication Code* is used in WPA2 to encrypt and check data integrity. It uses [[Encryption Algorithms|AES-CBC]] in counter mode to encrypt data and provide the MIC for the messages. This ensures that the MIC cannot be tampered with, as AES is considered to be one of the most secure encryption algorithms to exist today;
- **GCMP** (*Galois/Counter Mode Protocol*): this protocol uses the same encryption algorithm of CCMP, but uses a different code to generate the message MIC (*GMAC* - Galois Message Authentication Code). It is used in WPA3 and is considered to be faster and more secure than CCMP.

## WiFi Protected Access (WPA)

The WiFi Alliance provides certifications to devices that support different sets of authentication and encryption standards. When testing for these features, two authentication modes are defined:

- **Personal Mode**: the authentication uses secret keys that are generated from a PSK (Pre Shared Key). This way, if both devices know the PSK, they can generate the same secret and communicate;
- **Enterprise Mode**: the authentication uses the 802.1x format and the station must perform the key exchange with a authentication server on the network;

These sets are compiled to three major certifications:

- **WPA**: uses TKIP to encrypt data/generate MIC, and PSK (personal mode) or 802.1x (enterprise mode) for authentication;
- **WPA2**: uses CCMP to encrypt data/generate MIC, and PSK (personal mode) or 802.1x (enterprise mode) for authentication;
- **WPA3**: uses GCMP to encrypt data/generate MIC, and PSK (personal mode) or 802.1x (enterprise mode) for authentication. Also, it provides more security features to protect the wireless media, such as *Simultaneous Authentication of Equals*, which protects the initial [[PSK Four-way Handshake|PSK four-way handshake]].