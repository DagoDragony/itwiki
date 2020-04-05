# Network layers

There are 2 models TCP/IP(newer) and OSI(Open Systems Interconnection).
TCP/IP can be considered as condensed version of OSI:

## TCP IP

* Layer 1 Network access (or Link or network interface layer) It combines OSI model L1 and L2
* Layer 2 Internet Similar to OSI L3 
* Layer 3 Transport (or host to host) Similar to OSI L4
* Layer 4 Application (or Process layer) Combines OSI L5, L6, L7

## OSI

* Layer 7 (Application): Most of what the user actually interacts with is at this layer. Web browsers and other internet-connected applications (like Skype or Outlook) use Layer 7 application protocols.
* Layer 6 (Presentation): This layer converts data to and from the Application layer. In other words, it translates application formatting to network formatting and vice versa. This allows the different layers to understand each other.
* Layer 5 (Session): This layer establishes and terminates connections between devices. It also determines which packets belong to which text and image files.
* Layer 4 (Transport): This layer coordinates data transfer between system and hosts, including error-checking and data recovery.
* Layer 3 (Network): This layer determines how data is sent to the receiving device. It’s responsible for packet forwarding, routing, and addressing.
* Layer 2 (Data Link): Translates binary (or BITs) into signals and allows upper layers to access media.
* Layer 1 (Physical): Actual hardware sits at this layer. It transmits signals over media.

# VPN

* PPTP(Point to Point Telnet Protocol) - developed by microsoft, not so secure(basic encryption). Requires TCP 1723, easy to bock
* L2TP(Layer to Tunneling Protocol) - better version of PPTP. Uses UDP Port 500
* SSTP(Secure Socket Tunneling Protocol) - standart owned by microsoft, available for other platforms too. Highly secure. Uses port 443
* OpenVpn - uses 3rd party apps, strong encryption(AES), uses 443. Faster secure, cross-platform.

# TCPDUMP

graphite metrics search tcpdump -A -w results.txt 'tcp port 2003'

# Other tools

* dig - dns lookup utility
