
Active directory uses old protocol x.500 and LDAP
Allors centralized management for organization resources with authorization, authentication and accounting


## Remote Desktop

You can connect with RDP via:
-  `xfreerdp /v:<MS01 target IP> /u:<username> /p:<password>`


## Tools
- PowerView/SharpView: can be used to run windows net* commands
- BloodHound: visual map of AD to plan attack. Runs with SharpHound, C# agent that collects data. BloodHound also exists in python version in impacket.
- Kerbrute
- Impacket: python tools for network protocol interaction
- Responder: poison LLMNR, NBT-NS, MDNS
- inveigh.ps1: same as Responder
- InveighZero: C# version of inveigh
- rpcinfo
- rpcclient
- CME (CrackMapExec): toolkit for enumeration, attack and post-exploitation
- Rubeus: C# for kerberos attack
- GetUserSPN.py: impacket module for service principal
- enum4linux: enumeration for windows and samba systems
- enum4linux-ng: same but different
- ldapsearch
- windapsearch
- DomainPasswordSpray.ps1
- LAPSToolkit:  Powershell scripts to leverage Local Administrator Password Solution (LAPS) in AD
- smbmap
- psexec.py
- wmiexec.py
- Snaffler: AD information finding
- smbserver.py: SMB server execution, easy to share files
- setspn.exe: Access to Service Principal Names (SPN) 
- Mimikatz: pass the hash attack and others on Kerberos on host
- secretsdump.py: dump SAM and LSA secrets remotely
- noPac.py: exploit CVEs to impersonate DA
- rpcdump
- ntlmrelayx.py: SMB relay attacks
- PetitPotam: POC for some CVEs
- getgdpkinit.py: Cerficicates and TGTs manipulation
- getnthash.py: TGT -> PAC using U2U
- adidnsdump: dump DNS record from domain
- gpp-decrypt: Extract passwords and usernames from Group Policy Preferences files
- GetNPUsers.py: ASREPRoasting attack to obtain AS-REP hashes
- lookupsid.py: SID bruteforce
- ticketer.py: TGT/TGS ticket handling
- raiseChild.py: child to parent domain privilege escalation
- Active Directory Explorer: AD viewer and editor
- PingCastle: used for auditing security level of AD
- Group3r: AD GRO auditing
- ADRecon

## Recon checklists

- IP Space: ASN, cloud presence, DNS entries, etc
- Domain info: who is the domain admin?, subdomains, publicly accessible servers (mail, VPN, ...), defences in place
- schema format: username/password policies (from mail for example)
- data disclosure
- breach data