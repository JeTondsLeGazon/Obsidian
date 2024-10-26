Two types of general approaches in cryptography:
- Asymmetric key
- Symmetric key

## **Symmetric key**
Same key is used for both encryption and decryption, which leads so single point of failure
Suitable for performance and bulk data, easy to use

### Examples of use
- Payment application
- Hashing
- TLS (key exchange via asymmetric)

### Types of Encryption

#### Stream cipher
- one bit/byte at a time
- fastest
- Examples: RC4, Salsa20,

#### Block Ciphers
- encoding per chunk of fixed size
- size of block depends on key size
- each block encrypted then put back together
- Examples: AES, DES, 3DES, Blowfish


## Asymmetric key
Uses two different keys for en/de-cryption: public key for encryption and private for decryption

### Examples of use
- Document signature for authenticity
- Crypto-currency
- Browsing (SSL)
- Sharing symmetric key (TLS)
- ssh