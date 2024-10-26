
Service Network Management Protocol
Latest and safest version: SNMPv3
### Ports

- information transits via ...
- control commands via 161 / UDP
- server-side events via 162 /UDP (SNMP traps)

### Versions
- v1: no authentication / no encryption
- v2: same as v1, but community version exists with community string
- v3: authentication + encryption

### Tools
- **snmpwalk**: show info
- **onesixtyone**: can be used to brute-force usernames/password or community string
- **braa**
