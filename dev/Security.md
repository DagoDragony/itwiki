# Security

www.getsafeonline.org/protecting-yourself

Main Considerations
* Protecting against loss in sense that it need to be available to us
* Protecting against unauthorized access
* Protecting against unauthorized changes or coruption

## Telnet

Insecure shell sending everything in plain text
It's comfy to view package data with tcpdump

## Firewall

Firewall and IpTables are wrappers around netfilter which is a part of kernel.
Firewall blocks all incoming packets unless explicitly allowed
Packet outcomes
* Accept - accepted and passed to the port and a server to which it is addressed
* Reject - packet is rejected and sent back to the originator with a message that lets know
  what happened
* Drop - packet is dropped and proceeds no further. No msg is sent back to the originator.
  This is useful when blocking IP of known spammers. Their sending host must wait through timeout
  to try again, thus slowing down their attacks significantly
  
Firewall software
* iptables
* firewalld
* nftables
* fail2ban - dynamic firewall. It has configurable matching rules and separate actions that can be
  taken when attempts are made to crack into system. It has rules for many types of attacks that include
  web, email, other services vulnerabilities.

## PAM

Pluggable Authentication Modules - key component of security on Linux hosts and provides a dynamic
and flexible means to manage user access to their accounts and resources

PAM
* Account management - determines things like user's password is expired/locked and wheter the user is
  authorized to access a particular service
* Authentication management - task of authenticating the user, as in veryfying that password and user ID
  are correct. Can be extended to include biometric authentication, smart card hardware and methods
* Password mangaement - used in the process of password updates
* Session management - used to enable user access to services such as their home idrs, resources, allocation
  and deals with logging for audit trails

PAM configuration most likely be used mostly on resource management, such as CPU time, memory and number of
processes that specific user or groups may consume.
