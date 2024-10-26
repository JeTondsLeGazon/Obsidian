
## Goal
Find password of a newly created user `htb` (for pentesting)

## Steps

- Nmap reveals multiple ports: rpc, smb, rdp, nfs
- mounting nfs reveals a user named alex with its password
- this is used on smb to access some other creds
- trying the creds with username `Administrator` enables us to use rdp either via `xfreerdp` or `evil-rm` (as port 5985 is open) to connect
- With remote desktop, you check that `SQL Visual Studio` is pinned and can be accessed
- After searching through tables, could find table with usernames