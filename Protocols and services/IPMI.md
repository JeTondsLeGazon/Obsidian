
Intelligent Platform Management Interface: System's hardware monitoring and management

This is a service that can trigger software update for example

Used in three ways:
- Before OS booted to modify BIOS settings
- When host is powered down
- Access to host after system failure

port 623 UDP

System using IMPI protocol are called BMCs (Baseboard Management Controllers)

### Footprinting

- NSE: `ipmi-version`
- msfconsole: `auxiliary/scanner/impi/ipmi_version`

### Versions

__Default passwords__
- Dell iDRAC:  `root:calvin`
- HP iLO: `Administrator:<random 8 characters string with numbers and upper letters>`
- Supermicro IPMI: `ADMIN:ADMIN`

For HP iLO defaults: we can use Hashcat if we have the hash: ``hashcat -m 7300 ipmi.txt -a 3 ?1?1?1?1?1?1?1?1 -1 ?d?u

### Vulnerabilities

[IPMI 2.0 password hash leak](http://fish2.com/ipmi/remote-pw-cracking.html)
- Can then use Hashcat with mode 7300 offline
- See above for HP iLO
- Can be leveraged with msfconsole RAKP module