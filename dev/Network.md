# Network

Network layers
1. Application layer(Message)
   Http, DHCP, SSH, FTP, SMTP, IMAP
2. Transport layer(TCP segment) - provides end-to-end data transport and flow management services that are independent of the data and types of protocols being transported
   It uses ports such as 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 80 for http, 25 for SMTP 
   TCP, UDP
3. Internet layer(Packet) - packet routing, layer responsible for routing packets accross 2 or more different networks in order to reach their final destination
   It's about routers talking to routers in order to determina the next router in the chain
4. Data link layer(Frame) - manages direct connections between hardware hosts on a single, local, logical physical network
   This layer uses MAC address to identify the physical devices attached to the local network
   This layer cannot access hosts that are not on the local network
5. Physical layer(Bits) - hardware level consisting of NICs and the physical network cable as well as the hardware-level protocols used to transmit individual bits

Subnet mask
Eg. 192.168.2.64/26
Subnet mask in binary
11111111 11111111 11111111 11000000
First address is Network address 192.168.2.64
Last address is Broadcast address 192.168.2.127
Hosts are all between Network and Broadcast addresses

## DHCP

Used to configure the subnet mask, default gateway and dns server information on device
