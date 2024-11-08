
## Pentest steps
- Passive with Wireshark and TCPDump to check protocols/hosts/etc. Very useful for black box task
- Can also use Responder with passive mode options
- Once a list of hosts, either find other hosts (see `fping`), or start scanning
- Can brute force usernames with kerbrute, and then password spray
- Final goal is NT AUTHORITY\SYSTEM (local admin) and then domain admin


### SYSTEM-level admin escalation
- Windows exploit like Eternal blue
- Abusing running services
- Abusing SeImpersonate with [Juicy Potato](https://github.com/ohpe/juicy-potato)
- Others


Once a user is domain admin, he can:
- enumerate the domain (with tool such as Bloodhound for example)
- Kerberoasting
- SMB relay attacks
- gather Net-NTLMv2 hashes
- token impersonation
- ACL attacks

### LLMNR & NBT-NS Poisoning to obtain NTLM hash

- When on target network, can use tools such as responder (linux) and inveigh (windows) to get NTLMv2 hashes
- These hashes can be taken offline and cracked with hashcat and john

### Password spraying
- Better than brute force as will result in less lockouts
- Use linkedin / OSINT + jsmith.txt to find potential usernames
- Once list setup, try common passwords, while always waiting between rounds

If you can obtain the domain password policy, you can refine the password !
Better to wait a couple of hours between attempt to be sure the number of attempts has been reset

## Domain password policy

Can be obtained easily when SMB NULL or LDAP NULL (anonymous access without username/password). Great tools for these:
- rpcclient (`querydominfo`)
- enum4linux
- ldapsearch

### From windows
- `net use \\<host>\ipc$ "" /u:""`
- `net accounts`
-  powerview