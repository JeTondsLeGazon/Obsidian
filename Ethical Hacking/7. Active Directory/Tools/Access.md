
A few common tools may be used to access the target, or a computer of the target's network

### Remove Desktop Protocol (RDP)

Accessible on port 3389, can open a desktop windows on the target:

`xfreerdp /v:<target IP> /u:<username> /p:<password>`

### Evil-winrm

Shell for windows written in Ruby. Can be used through remote WinRM (Windows Remote Management) port 5985.
Opens a shell on the target with special commands with:
`evil-winrm -i <ip> -u <username> -p <password>`

Check all information on the [source code](https://github.com/Hackplayers/evil-winrm)
