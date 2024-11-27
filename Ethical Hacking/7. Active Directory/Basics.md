Active Directory (AD) is a directory service developed by Microsoft for windows domain networks. It uses a client-server architecture and is commonly used by enterprises to handle authorization, authentication and access.

AD uses different kind of technologies/services to run effectively:
- Lightweight Director Access Protocol (LDAP)
- Kerberos
- DNS
- RPC

## Server
The server running Active Directory Domain Services (AD DS) is called the domain controller (DC). When a user is logged into the AD (through this server), we say it is domain-bound.

## Objects

RID = relative ID (hex), which, with the domain SID, give to each object a unique identifier when both are combined
Some accounts have the same RID always, such as Administrator (0x1f4)

### Service Principal Name (SPN)
A service principal name is a unique identifier for a service instance, as opposed to user objects. With them, we can allow a client application to authenticate
AD users can therefore have a SPN when they run services, such as MS SQL. But they generally don't have any.

Domain users will however always have a User Principal Name.
