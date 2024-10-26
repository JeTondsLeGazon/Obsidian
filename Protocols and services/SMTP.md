Basic SMTP does not use encryption, which is why nowadays we usually talk about Extented SMTP (ESTMP)

Can be reached by telnet, usually on port 25

Commands:
- HELO or EHLO to start connection
- VRFY: enumerate users

### User enumeration
- nmap --script smtp-enum-users.nse
- msfconsole user enumeration
- CLI programm smpt-user-enum
