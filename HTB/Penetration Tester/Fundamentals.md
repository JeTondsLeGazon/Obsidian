
### Shells

- bash or powershell accessible through ssh and winRM repectively
- Apart from the above, we have three types of shells:
	- reverse shells
	- bind shells (wait for us to connect)
	- web shell (web server http input + output print)
 
 
### Bind shells

 Once we have set up a bind shell (check payload of all things), we have **to connect to it** with netcat: `nc $IP $PORT`
Unlike reverse shells, if the connection drops, we can connect back to it.


### TTY
Once we get a shell connection outside ssh/winrm, we cannot use command history nor edit our current input. For this we need to upgrade our TTY by mapping our TTY with the remote TTY.

- python/stty with `import pty; pty.spawn("/bin/bash")`
- ctrl+z to background netcat connection
- `stty raw -echo`
- Bring back netcat command with `fg`

If we want to size parameters as well, use echo $TERM locally and set the same variable remotely, same for stty size

### Web shells

Upload the script (php, jsp, ...) to some web server root directory if possible:
- Apache: /var/www/html
- Nginx: /usr/local/nginx/html
- IIS: C:\\inetpub\\wwwroot
- XAMPP: C:\\xampp\\htdocs

## Privilege escalation

Checklists available on:
[hacktricks](https://book.hacktricks.xyz/)
[PayloadOfAllThings](https://github.com/swisskyrepo/PayloadsAllTheThings)

For both Linux (goal: Root) and Windows (administrator/SYSTEM)

On linux, [GTOBins](https://gtfobins.github.io/) gives list of commands that can be abused with sudo access to become root. Same on Windows with [LOLBAS](https://lolbas-project.github.io/#)


### File transfer

- Python http server + curl/wget on remote
- SCP if we have ssh credentials `scp linpeas.sh user@remote-ip:/home/user/linpeas.sh`
- base64: if we cannot upload some file, we can copy-paste the file through base64 encoding + decoding on remote
We can check file type with `file` command

After a transfer, can check file md5sum on remote and local to ensure it is valid

