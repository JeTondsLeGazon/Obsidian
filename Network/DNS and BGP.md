
## DNS information and records

- SOA: start of authority -> which nameservers are responsible for domain
- MX: mail exchange -> mail server
- PTR: pointer records -> CNAME record for given IP
- CNAME: canonical name of records -> alias for another host
- AAAA -> IPV6
- SPF: sender policy framework -> ...

DNS can be retrieved from dns server either partially with a query (`dig`, `dnsrecon` or available sites), or fully with a zone transfer (axfr).
Two other ways to find domain names are through DNS brute force and search engine use (with `theharvester` for example).

## BGP
Border gateway protocols can be used to gain insight against targets website.
BGP are path from src to dst and the protocol aims to find available/optimal paths around subnets.
Uses port 179 TCP
BGP uses Autonomous Systems (ASs), which are subnet protocols that respond to BGP and give it its neighbours.
BGP looking glass servers are useful for that, which can be pinged with telnet (check list on google).
These are servers made available by university, research group or gov.

**Whois** and **show ip** can be both used with AS and BGP to have details about them
## Examples
### FROM APT BOOK
- target is California department of motor vehicles (DMV)
- Find related IP with `nslookup dmv.ca.go`
- check BGP info with `show ip bgp <ip>`
- output shows a lot of `3277 3267 9002 7385 1226` numbers (which are paths with AS numbers), a lot of those ending with 1226, which is the last public hop for target subnet. 
- may be ASN of target org, find out with `whois AS1226`
- We can find all other networks for those `AS1226` is the final hop with `ip bgp regex _1226$`
- There we go: without sending single packet to target, we may have found 24 other public subnets where target may have resources on. Be extra sure by using `whois` on all of these to see if they are related to target.