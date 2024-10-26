Each file in the filesystem in Unix has some privileges, marked as a triplet of `rwx` with a leading `-` or `d` (directory).

Example (from `ls -a`):
`drwxrwxr-x`

The first triplet represents the file owner, the second the file's group and the last everyone else.

The triplet can be used in binary form to give a number. `rw-` would be `110`, or 6
#### Change them
Permissions can be changed using the `chmod` command (change mode)

Example:
`chmod +x myfile.txt` to make `myfile.txt` executable
`chmod 777 myfile.txt` to give all permissions to the file
`chmod 741` to give: all to owner, read only to group and execute only to all other users 
`chmod +s /bin/bash` to give **owner's** permission instead of user's (in this case, any user executing `bash -p` would have root privileges as `/bin/bash` has been (usually) created by root)


## Users

Can edit /etc/passwd with plaintext hashed password to add another user with root privileges:
	echo "thor:<mypassd>:0:0:thor:/root:/bin/bash" >> /etc/passwd

with <mypassd> generated from `openssl passwd <non-hashed-passwd>`


All users within /etc/passwd are stored as:
`name:passwd:UID:GID:info:homedir:shell`