The management framework has many messages that can be exchanged between the [[Network Management Station (NMS)|NMS]] and the managed devices.

They include, but are not limited to:

- **Read**: this type of message intends to read information from a [[SNMP|MIB]] of a managed device;
	- For example, `Get`,`GetNext` and `GetBulk`;
- **Write**: there is only one type of write message: the `Set` message. Used to configure managed devices remotely;
- **Notification**: these messages are sent from managed devices to the NMS. They are configured events that trigger a notification on the NMS once they happen, for example an interface going down;
	- For example, `Trap` and `Inform` are notification messages;
- **Response**: finally, response messages are sent in response to previous messages;
	- This is because SNMP uses UDP, so it does not have message delivery guarantee;
	- The response message is called `Response`;

