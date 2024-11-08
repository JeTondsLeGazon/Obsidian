
- First need to run nmaps to discover IMAPs/POP3s ports open, with SSH as well.
- Here need to use UDP scan to find that SNMP is open as well.
- use onesixtyone for community discovery and find `backup`
- use `snmpwalk` with this community string to find password for user `tom`
- use this password+username to connect to IMAP via `openssl s_client`
- look around and find an ssh key to be used for SSH and user tom
- check running processes to find out that mysql is running
- connect with tom+password and list creds