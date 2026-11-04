# Router
it manages traffic between diferent networks
it uses Routing Table
## Routing Table
It is set of rules by with the router determine where to send said packets

| Destination   | Subnet          | Interface |
| ------------- | --------------- | --------- |
| 128.75.43.0\| | 255.255.255.0   | Eth0      |
| 128.75.43.0   | 255.255.255.128 | Eth1      |
| 192.12.17.5   | 255.255.255.255 | Eth3      |
| Default       | 0.0.0.0         | Eth2      |
The Subnet Mask of default route is always 0.0.0.0