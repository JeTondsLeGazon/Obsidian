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

### Access Control List (ACL)

The ACL holds all permissions for users in AD. Each entry is called Access Control Entry (ACE), meaning that each object has an ACL but can have many ACE

## Kerberos
Kerberos is a microsoft AD protocol for authentication that works without ever sending the password through the connection.

Kerberos is a network authentication protocol that uses symmetric cryptography to secure communications between the client and server, using a central key distribution center (KDC). The KDC acts as an intermediary between clients and other servers on the network. 

![[kerberos.png]]

1. Client sends authentication request to the Authentication Server (AS) containing AES or DES encrypted credentials
2. AS verifies identity of the user (authentication) and issuse a Ticket Granting Ticket (TGT), which will be stored on the client's computer to be used for future request (acts like a master key).
3. The client, using the TGT, request a service specific ticket to the Ticket Granting Service (TGS).
4. TGS verifies the TGT validity and the resource. If successful, TGS sends back a service-specific ticket (encrypted with service's secret key)
5. Received service-specific ticket sent forward to service, which verifies it with its secret key

TGT is usually related to SPN

#### TODO: finish

## LDAP
Stands for Lightweight Directory Access Protocol, which registers user information accross AD

Used for:
- user management
- group management
- Authentication and Authorization
- SSO
- Network Access Control
