
Point of connection between machine (computer) and a network (public or private). Generally physical with the Network Interface Card (NIC), but can also be software like the loopback address (IPV4 127.0.0.1)

When running commands to show available network interfaces (`ifconfig`), we usually see:
- lo: loopback address
- eth0: ethernet 0

When connected to a NI, any device on this network cannot communicate with a device on this computer on another network (isolation).
However, when connected to 0.0.0.0, a service will be attached to all network interfaces
## Commands:
- `ipconfig`
- `tcpdump`: network packet sniffer
- `tshark`: CLI version of wireshark, less flexible but maybe more complete than `tcpdump` with filters
- `netstat`
- `iftop`: top command but for network
- `ip ad`

[Mini-guide of all commands](https://gist.github.com/tianchaijz/a8b239d703024ec405f5037118f84a1c)

