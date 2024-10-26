
6 layers for enumeration:
- internet presence
- gateway
- accessible services
- processes
- privileges
- os setup

### Certificates
Always check certificate on HTTPS connection to check for subdomain + check if valid certificate on crt.sh


## Internet presence (OSINT)

### Checklist
- dig
- host
- shodan
- HaveIBeenPwned
- Dehashed
- BGPToolkit
- domain glass
- domain/subdomains list (HTTPS, google, ...)
- GrayHatWarfare


Use combination of domains/subdomains, host (DNS resolution) and shodan

![[Pasted image 20240831141205.png]]

We can also use dig

![[Pasted image 20240831141239.png]]

NS: nameserver for FQDN to IP resolution : often info about ISP


We can also look at domain glass