
- Python, Perl, Ruby, PHP, VBScript (Windows), ...


### Netcat

On receiving machine: `nc -l -p <port> --recv-only > myfile`
On sending machine: `nc -q 0 <othermachine-ip> <port> < filetotransfer`
Alternatively use `--send-only` instead of `-q 0

We can do the reverse and expose a file on listening server and get it on client side

### /dev/tcp

Sending: `cat < /dev/tcp/<ip>/<port> > file`