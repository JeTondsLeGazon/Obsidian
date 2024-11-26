Active Directory (AD) is a directory service developed by Microsoft for windows domain networks. It uses a client-server architecture and is commonly used by enterprises to handle authorization, authentication and access.

AD uses different kind of technologies/services to run effectively:
- Lightweight Director Access Protocol (LDAP)
- Kerberos
- DNS
- RPC
### Server
The server running Active Directory Domain Services (AD DS) is called the domain controller (DC). When a user is logged into the AD (through this server), we say it is domain-bound.

### Hierarchy
The goal as a pentester if to target a local `NT AUTHORITY\SYSTEM` admin and move our way up to the domain admin.