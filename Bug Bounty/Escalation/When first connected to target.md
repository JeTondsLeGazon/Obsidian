* When connected to target, always begin with `sudo -l` to check your rights
* Check as well root: `ls -la /` for weird files (entrypoint.sh could mean inside docker)
* You can then consider `linpeas.sh`
* Remember that docker `docker --version` can also be exploited if you know it is on the system

## Escalation
- check kernel version
	- needed:
		- vulnerable kernel
		- exploit available
		- can transfer exploit on target (which is why blocking FTP, wget, curl, ... can be important)
		- can execute it
- .Xauthority file is related to the X window management system (GUI). You can `export XAUTHORITY=.Xauthority` and then get the view with `w` . You can then get a screenshot of the display with the `xwd` command
- If user has all right --> `sudo -i` will yield a root terminal

### List services
- `ss -ltup` or `netstat -ant`

### Forward port / install exploit
- `chisel` can help to forward port
- `curl` or `wget` to download from localhost (`python3 -m http.server`)