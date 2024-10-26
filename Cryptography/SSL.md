Secure socket layer
Developed to encrypt data between server and client
Works between transport and application layer (we have there SSL layer)

Cons:
	- authenticity by securing connection
	- confidentiality of information
	- integrity of data

## Steps
1. Client and server sends hello signal
2. Client sends data information: SSL version, cipher suite, session ID, etc.
3. Server returns encryption algorithm from cipher suite and a compression algorithm
4. Server sends authentication certificate and requests it from client 
5. Server sends public key for encryption
6. Client sends own certificate after veryfing server with CA (certificate authorities)
7. Client sends secret private key encrypted  using server's sent public key
8. Finished signal from both sides

TLS is successor of SSL