

### SYSTEM-level admin escalation
- Windows exploit like Eternal blue
- Abusing running services
- Abusing SeImpersonate with [Juicy Potato](https://github.com/ohpe/juicy-potato)
- Others


Once a user is domain admin, he can:
- enumerate the domain (with tool such as Bloodhound for example or windapsearch)
- Kerberoasting
- SMB relay attacks
- gather Net-NTLMv2 hashes
- token impersonation
- ACL attacks

### LLMNR & NBT-NS Poisoning to obtain NTLM hash

- When on target network, can use tools such as responder (linux) and inveigh (windows) to get NTLMv2 hashes
- These hashes can be taken offline and cracked with hashcat and john




#### Password spray technique

The following tools/methods can be used;
- For loops over valid users with rpcclient + `-c "getusername; quit"`: 
	- `for u in $(cat valid_users.txt);do rpcclient -U "$u%Welcome1" -c "getusername;quit" 172.16.5.5 | grep Authority; done
- crackmapexec
- kerbrute

## Domain password policy

Can be obtained easily when SMB NULL or LDAP NULL (anonymous access without username/password). Great tools for these:
- rpcclient (`querydominfo`)
- enum4linux
- ldapsearch

### From windows
- `net use \\<host>\ipc$ "" /u:""`
- `net accounts`
-  powerview


## After initial access

After foothold has been achieved with a user with lower privileges, it is time to query the AD (smb, ...) for more:
- CrackMapExec: with `-U <username> -p <password>` to query usernames, groups, logged on users, ...
- BloodHound: can be used to recover active sessions (logged on users)
- SMBmap
- Impacket: (psexec, wmiexec)
	- psexec: Create remote connection to host (via RPC) and give us an interactive remote shell as SYSTEM. Need a user with local admin privileges

#### Windows
- ActiveDirectory module for powershell
- powerview
- Snaffler (for credentials hunt in shares)
- BloodHound (for visualization) with SharpHound (for data collection)

### RPCclient
- Always good idea to try SMB NULL session
- RID = relative ID (hex), which, with the domain SID, give to each object a unique identifier when both are combined
- Some accounts have the same RID always, such as Administrator (0x1f4)


## Windows: living off the land
- powershell can be downgraded with `powershell.exe -version 2`. Interesting as version 2 does not have log system enabled, meaning we will be stealthier
- Check defenses with `netsh` and `sc`
- Check network with: 
	- `arp -a`
	- `route print`
	- `ipconfig /all`
- Check WMI: Windows Management Instrumentation
- `Net` commands