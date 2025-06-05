The final goal for a machine is to get to  `NT AUTHORITY\SYSTEM` 

## Gather additional information

Once we have gained access and got credentials, we can gather more information or connect to the host with the following methods:
 - **CrackMapExec**: with `-U <username> -p <password>` to query usernames, groups, logged on users, ...
- **BloodHound**: can be used to recover active sessions (logged on users)
- **SMBmap**
- **Impacket**: (psexec, wmiexec)
	- psexec: Create remote connection to host (via RPC) and give us an interactive remote shell as SYSTEM. Need a user with local admin privileges

#### Windows
- ActiveDirectory module for powershell
- **powerview**
- **Snaffler** (for credentials hunt in shares)
- **[[BloodHound]]** (for visualization) with SharpHound (for data collection)

## Privilege escalation
- Try [[LLMNR & NBT-NS Poisoning]]
- Retry password spraying and hope to find an admin account
- Windows exploits, such as Eternal Blue
- Abusing running services (normal privesc)
- [[Kerberoasting]]
- Abusing `SeImpersonate` (check with `whoami /all`) with [Juicy Potato](https://github.com/ohpe/juicy-potato)
- Find other vulnerabilities with standard method or through `winpeas` (normal privesc)

Maybe more interesting once admin, but still worth it:
- SMB relay attacks
- gather Net-NTLMv2 hashes
- token impersonation
- ACL attacks


## Living off the Land (LOTL)
- powershell can be downgraded with `powershell.exe -version 2`. Interesting as version 2 does not have log system enabled, meaning we will be stealthier
- Check defenses with `netsh` and `sc`
- Check network with: 
	- `arp -a`
	- `route print`
	- `ipconfig /all`
- Check WMI: Windows Management Instrumentation
- `Net` commands (accounts, group, localgroup, ..)
- [`dsquery`](https://www.aud507.com/media/DSQuery.pdf)
- [Get-MpComputerStatus](https://docs.microsoft.com/en-us/powershell/module/defender/get-mpcomputerstatus?view=windowsserver2022-ps): check defenses

For other Powershell commands, check [[Powershell Cheatsheet]]
