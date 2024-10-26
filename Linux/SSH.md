
SSH (secure shell) protocol is used for computer-computer communication via encrypted tunnel

As an authentication mechanism, SSH can either ask for keys, password, or both.

#### Keys

SSH keys are composed of a private and public key, the public key belonging to the target server and the private to the client wanting to connect

If a private key is stolen, another user could use `ssh ... -i stolen_key` to connect (! `chmod 600` the stolen key file first)