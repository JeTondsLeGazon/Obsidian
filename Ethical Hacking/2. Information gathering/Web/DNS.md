
## DNS
- `whois`
- `nslookup
- `host
- `dnsenum
- `fierce
- `dnsrecon
- `theHarvester`

### DNS zone record
Check their signification [here](https://www.cloudflare.com/learning/dns/dns-records/)

![[image_dig.png]]

### Host file

windows host file located at C:\Windows\System32\drivers\etc\hosts


## Virtual host (vhost)

For virtual host discovery (virtual host = same IP), gobuster may be better if the target need a specific port, as by experience could not make this work with ffuf:

Standard port:
`fuff -u http://FUZZ.<target> -w /.../subdomain-list -H "Host: FUZZ.<target>"

With port:
`gobuster vhost -u http://FUZZ.<target>:<port> -w /.../subdomain-list --append-domain`

