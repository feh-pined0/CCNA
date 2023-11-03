The Domain Name System follows a very specific disposition of global servers to make sure that names all across the internet can be resolved to their correct destination. **Name Servers** are placed in a hierarchy so that each server holds a "piece" of information about a domain. Join all pieces together and a name is resolved.

The following types of name servers are defined:

- **Root Name Server**: these name servers are the initial step to resolving any WAN (no pun intended) domain name. There are 13 sets of root name servers, that are operated by 12 organizations world wide. These servers point to the **TLD server for the name queried**;
	- The address to those server are: `LETTER.root-servers.net`, where `LETTER` is replace with any letter from `a` to `m`;
	- Also these servers all have a `.org` page to display some information about the servers and the organizations behind it, like `a.root-servers.org`;
- **TLD (Top Level Domain) Name Server**: these servers hold information about DNS names using the top level domain they administer. For example, the `.com` TLD hold authoritative server information about all DNS names that use `.com`, like `google.com` or `youtube.com`. These servers point to the authoritative server that holds the DNS information about a domain name;
	- These also include ccTLD (Country Code Top Level Domains) like `.com.us` or `.com.br`;
- **Authoritative Server**: the final server in the chain, the authoritative server holds information about DNS mappings. The process for registering a DNS name usually involves setting the DNS name to host's IP mapping on one of this authoritative servers, which then advertises this mapping for the adequate TLD server, so that it can correctly query the right authoritative server when resolving;