To make a website trustworthy, we usually use the prefix `https` instead of `http` (`s` for secure). Behind this single letter lies a new connection type, SSL/TLS.

SSL/TLS connections resort on certificates to encrypt the connection between a browser and the server to avoid MitM attacks. These certificates are distributes by specific authorities.

## Certificate authorities (CA)

Certificate authorities deliver their signature to sign certificates.
In fact, only the end-entity or intermediate CA deliver certificates to users. CA form a chain, with at the top the root CA, which delivers certificates to other trustworthy CAs and so forth.

## Certificate transparency logs

Store for CAs that browser will use to check the authenticity of the certificate.

Can be usefeul to dig through to gather web intelligence, using either of:
- `crt.sh` (web page [here](https://crt.sh/))
- `censys`

## Digital certificates

![[certificate.png]]

A certificate is the organisation information along its public key transmitted to a CA. The CA then encrypts everything using the private key which forms a signature appended to the certificate.