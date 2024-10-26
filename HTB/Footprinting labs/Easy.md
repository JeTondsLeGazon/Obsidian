
**Goal**: Find `flag.txt` file on remote DNS server of company `inlanefreight.htb`. We know some creds: `ceil:qwer1234`

### Steps

- Run nmap on IP and see we have: ftp, ssh, dns, ftp-proxy
- See that the creds yield nothing on ftp and ssh accepts only keys
- `dig axfr @$IP inlanefreight.htb` to discover subdomains
- grep them + tr them to have one line added to `/etc/hosts`
- for each subdomain (or select interesting one), try `dnsenum` to find other subdomains
- see that `ftp.internal.inlanefreight.htb` could be interesting and try `ftp` on it -> nothing
- redo last step on `ftp-proxy` (port 2121) and see it works (creds above)
- take ssh key, chmod it + ssh