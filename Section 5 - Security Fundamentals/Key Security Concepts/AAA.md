*Authentication, Authorization and Accounting* is a key security concept. Actually, it defines three coupled concepts that complement each other:

- **Authentication**: is the act of verifying the authenticity of the user. It is basically the act of proving the user (or device) is who they say they are.
	- A login attempt is an example of authentication;
- **Authorization**: is the act of granting users access to services and information based on they access level.
	- Authorization does not require user authentication to happen first. A guest user can be granted (authorized) access to some basic services without authentication;
- **Accounting**: the act of logging activity information about users and what they did in a system over time. This is basically logging (see [[Syslog]]);

Usually, AAA is performed using a centralized server (see [[RADIUS]] and [[TACACS+]]).

