
Have a look at DNS first [here](obsidian://open?vault=Obsidian%20Vault&file=Network%2FDNS%20and%20BGP)

### Types of DNS servers:
- Root server: responsible for Top-Level-Domains TLD, there are 13 of them
- Authoritative name servers: responsible for a zone. if cannot answer, request passed to root server
- non-authoritative: not responsible for a particular zone. They do some DNS querying
- caching DNS server: cache information from other servers for a period of time, determined by authoritative server.
- forwarding: forward request to another server
- resolver: perform name resolution locally in computer/router


DNS mainly unencrypted, but now TLS (DOT) or https (DOH) applied.

### Local DNS resolution example

If your computer DNS fails to resolve a hostname, it will fallback to some protocols:
- mDNS: multicast DNS
- LLMNR: link-local multicast name resolution
- NBT-NS: Netbios name service
These protocols send DNS query to other computers on same subnet

##### Poisoning
This can be leveraged by responding by own IP. The target may then try authenticate to our machine and send NTLMv2 challenge/reponse which we may crack offline

To mitigate these MITM attacks, these protocols should be disabled

Moreover, these attacks works when on the subnet directly, not over VPN because these are layer 2 protocols (which do not cross VPN).
### DNS records

![[Pasted image 20240912073615.png]]