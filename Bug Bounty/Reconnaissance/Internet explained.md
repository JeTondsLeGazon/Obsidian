1. A request is done from your browser (mydomain.com)
2. Your browser will check its cache (with your os) to check if this domain name is stored somewhere (name -> ip address)
3. If not, your dns resolver (usually your Internet Service Provider (ISP)) will be called to check if it knows the domain name in its cache
4. If not, the resolver will ask the root server (there are 13 root servers existing, named from A to M), which knows where to find TLD (top-level domain) servers (.COM, .NET, ...)
5. These TLD know the authoritative name servers for `mydomain.com`, like:
* `ns1.mydomain.com`
* `ns2.mydomain.com`
* `ns3.mydomain.com`
6. `WHOIS` command gives you these authoritative servers

## Zone Transfer
Zone transfers = replicating DNS records across DNS servers, using AXFR protocols