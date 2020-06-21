# Security

www.getsafeonline.org/protecting-yourself

Main Considerations
* Protecting against loss in sense that it need to be available to us
* Protecting against unauthorized access
* Protecting against unauthorized changes or coruption

## Telnet

Insecure shell sending everything in plain text
It's comfy to view package data with tcpdump

## Firewalls

Firewall and IpTables are wrappers around netfilter which is a part of kernel.
Firewall blocks all incoming packets unless explicitly allowed
Packet outcomes
* Accept - accepted and passed to the port and a server to which it is addressed
* Reject - packet is rejected and sent back to the originator with a message that lets know
  what happened
* Drop - packet is dropped and proceeds no further. No msg is sent back to the originator.
  This is useful when blocking IP of known spammers. Their sending host must wait through timeout
  to try again, thus slowing down their attacks significantly
