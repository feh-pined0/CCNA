*Authentication* is the act of verifying the authenticity of the identity of a peer. For example, when a page requires a login with username + password credentials, the page is *authenticating* the user, to verify that they really are who they say they are.

Authentication can occur in various forms. The most common ones today are:

- **Username/Password Credentials**: here, an entity is required to input a username and password combination that identifies it. It's the most common for most user based authentication;
- **Digital Certificate**: in this case, the entity presents a digital certificate that identifies itself. This certificate must be signed by a certificate authority to authenticate this certificate and ensure that this entity is really who they say they are. Generally, these certificates are composed by information about this entity (such as organization names, DNS names, state and country information) and a [[Asymmetric Key Pairs|asymmetric key pair]].