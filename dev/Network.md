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
Dynamic Host Configuration Protocol

Used to configure the subnet mask, default gateway and dns server information on device
Provides a centralized and automated method for configurint hosts when they connect to the network

Obtaining ip process
* DHCP Discover - send broadcast message to all network pc's in hope for dhcp server to respond
  Others pcs ignore this message
* DHCP Offer - when dhcp get message it sends back the message for the host with specific ip offer
  If more offers received, host chooses first received
* DHCP Request - host says ok to ip and sends request to DHCP Server
* DHCP Acknowledgment - DHCP server sends the host back ip address, subnet mask, default gateway and the dns server
  DHCP Server saves all ip addresses and Lease time, Lease time is the time host needs to renew his ip
  address, otherwise it will return to available ip adresses pool

`/etc/dhcpcd.conf` 
Parts
* DHCP Client - uses UDP 68
* DHCP Server - uses UDP 67

## NAT
Network Address Translation

* Overload (PAT - port address translation) - on of the most popular version of NAT
  Router has NAT table
	* it swaps local ip to public with the same port(increased by one if same is used)
	* saves request From To info
	* reformat package and send to destination
	* when request is back it sends the package back to local ip
* Dynamic NAT - 

NAT converts private addresses to public addresses

Private addresses - servers purpose of prolonging IPv4

Internet provider usually gives 1 public address

## Name search

1. Type address
2. Browser sends the request to OS
3. OS checks /etc/hosts if host name is found returns IP to browser
4. If not found in /etc/hosts, it searches in first name server of /etc/resolve.conf
5. Local name server sends the request to a remote name server
6. Root name server returns IP address of the authoritative name server for given address
7. The browser uses the IP address to send a request for a web page which  is downloaded to browser
