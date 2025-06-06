
IMAP: Internet Message Access Protocol
POP3: Post Office Protocol

IMAP used for email management, but unlike POP3, allow direct mail management on the server

### Access
Can even use URIs  `imaps://<IP>`
`curl -k imaps//<IP> --user <user>:<password> -v` (-k to disable ssl certificate verification)

Can use telnet or `openssl s_client -connect $IP:imaps`

Then commands listed (all commands should begin with random tag) [here](https://www.atmail.com/blog/imap-commands/)
### Ports: 
- 143 / 993 for IMAP
- 110 / 95 for POP3
	higher ports for TLS/SSL encryption 


Works unencrypted -> need TLS/SSL to encrypt 


## IMAP CLI

Once connected with `openssl`, we can login with `<tag> LOGIN <username> <password>`, where `<tag>` can be anything (should not even remain the same for all commands)

- List all mailboxes with `<tag> LIST "" *`
- Select mailbox: `<tag> SELECT <mailbox>`
- If messages from above command (`<exists>` > 0): `<tag> FETCH <number> (body[])`

