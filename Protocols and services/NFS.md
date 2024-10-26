Acts like SMB as a filesystem shared across the internet. However, purely Linux/Unix and uses a different protocol. Since version 4, can be used jointly with Kerberos.

Uses port 2049 and for version<4, uses port 111

NFS protocol has no authentication mechanism, this is delegated RPC protocol behind (ONC-RPC/SUN-RPC). Most of the time will rely on UID/GID

### Dangerous settings

- rw: read-write access (compared to ro: read only)
- insecure: can use ports above 1024 (which can be set by any user, <1024 only root)
- nohide: if another folder mounted below another one, will be exported via its own entry
- no_root_squash: remote users will be root and created files will have UID/GID 0

### Exploit

To check which folder where mounted by a target, we can use `showmount -e $IP`

Then to mount the filesystem: `mount -t nfs $IP:/path/to/share ./mylocaldir -o nolock`

To unmount it: `unmount ./mylocaldir`