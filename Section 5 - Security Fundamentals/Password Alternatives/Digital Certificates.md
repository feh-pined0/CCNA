*Digital Certificates* are mainly used to authenticate websites to accessing users, but can be used to authenticate anything (devices or users). The important part of a digital certificate that guarantees authenticity is the process of making one:

- Companies or Users will generate a **CSR** (*Certificate Signing Request*) and send it to a **CA** (*Certificate Authority*);
- This CA will make tests to make sure that the domain, user or device is who they say they are;
- After these tests, the CA will sign the certificate using a [[Asymmetric Key Pairs|asymmetric key]];
- These CAs are globally trusted by manufactures all around the earth.
- If a digital certificate is signed by one of them, it means they are legit;

Here is an example of a digital certificate:

![[Digital Certificate.png]]

This certificate was signed by Google for Google. But the Google CA's certificate was signed by a globally trusted CA Root (GlobalSign Root CA). This categorizes a **Certificate Chain**.