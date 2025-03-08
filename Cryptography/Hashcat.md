
Hashcat can support the format `(user):hash`, simply run hashcat with the flag `--user` to say the first part before the colon is the username


### PBKDF2
Sometimes, from SQLite, we have this algorithm and the password and salt are both in hexadecimal format instead of base64.
Therefore, we need to run `xxd -r -p | base64` on both of them to:
- convert them back into binary
- convert them into base64

Then the hash has the following structure:
`sha256:${nb_round}:${salt}:${digest}`
where `nb_round` is the value just after the algorithm name in the table


