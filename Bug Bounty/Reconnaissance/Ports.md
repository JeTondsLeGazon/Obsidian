- 53: tcp/udp | DNS: used by dns to initiate zone transfer. If open, can try a zone transfer to get subdomain
- 139: SMB
- 445 SMB
- 5985-6: winRM

### Android
- 5555: ADB (android debug bridge), can connect with adb
- 59777: ES file explorer vulnerability, which lets port open


## Scanning
### Nmap
If not run as root, will perform -sT (TCP scan), otherwise -sS (SYN scan)

Available options to know:
* -A: OS detection, version detection, script scanning and traceroute
* -v: gives us which port is open
* -sn: disable port scanning. If used, nmap will automatically ping scan with ICMP echi requests (-PE). Note that determinin g if the host is alive would usually be used by ARP pinging, which is the first packets sent by nmap
* --packet-trace: show all packets that are sent/received.
* --reason: explains
* --disable-arp-ping: disable arp pinging, which could lead to ICMP
* --top-ports=x: only scan the top x ports
* -Pn: disable ICMP echo requests
* -n : disable DNS resolution
* --min-rate: set nb of packets to send per second
* -D: decoys to mimic multiple IP addresses (RND:5 for example)
* -g: specify the source port we want to scan from. Some misconfigured firewall could filter responses except for some incoming ports (like 53 = DNS)

TCP connect is the most accurate scan to determine state of port and the stealthiest because does not leave unfinished connections

Space bar [space] during nmap scan will show the progress, which also be achieved with --stats-every

#### NSE

Useful scripts:
- version
- banner
- smtp-commands
- safe
- 

### Banner Grabbing

- nmap can usually give us information on banner
- tcpdump + netcat can help us leverage additional information