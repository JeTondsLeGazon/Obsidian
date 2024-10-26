
Capabilities enable process/file for only certain features/restrictions. Important because we can give only the minimum capabilities to a file/process given its requirements.

### Commands
`getcap` <filename/binary>: list capabilities of a file
`getcap -r`: recursive
`getpcaps` \<process id\>: list capabilities of a running process
`setcap cap_net_bind_service+ep /usr/bin/my_binary` : enable service to bind socket with port <=1024. `ep` means effective process

### Some capabilities

`CAP_SETUID`: process can set uid
`CAP_CHOWN`: can change file ownership
`CAP_KILL`: can kill process

EUID vs UID: EUID for effective UID is a dynamic identifier for a process at a given time.
