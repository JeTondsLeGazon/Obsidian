When we are connected on target network, we can investigate which protocols are used with responder (passive mode), tcpdump or wireshark.

There are two interesting protocols we are looking for:
- LLMNR: Local-Link Multicast Name Resolution
- NTLM: New Technology LAN Manager

Both of these are broadcasted when the local DNS fails to resolve a host and the machine asks the subnet. Of course, some options need to be configured as we don't want that if possible as we can poison the response.
By using responder, we can create a MitM attack by responding to these calls. The target machine will then send its NTLMv2 hash to authenticate, which we can take offline to crack

## Tools
- Responder (Linux)
- Inveigh (Windows)