# Networking

A *packet* is a unit of data that is sent over a network. If an entire message is too large to send at once, the message is broken down into chunks. Each chunk is packaged with a header, payload, and trailer. 

A packet follows the same concept of a postal letter: the header is the envelope, the payload is the letter, and the trailer is the signature. 

## ping 

`ping` is the most basic network command. It sends a special network packet called an ICMP ECHO_REQUEST to a specified host. Most network devices receiving this packet will respond to it, allowing the network connection to be verified.

It is possible to configure most betwork devices to ignore these packets, usually done for security reasons to partially obscure the host from a potential attacker. It's also common for firewalls to be configured to block ICMP traffic.

When you ping a site, ping continues to send packets at a specified rate (default 1s) until interrupted. Once interrupted, ping prints performance statistics, such as the number of packets transmitted, the number of packets received, the percentage of packet loss. 

A properly performing network will have 0% packet loss, and a successful ping indicates that the elements of the network are in good working order.

## traceroute or tracepath

`traceroute` or `tracepath` lists all the hops network traffic takes to get from the local system to a specified host

## Transporting files over a network

`ftp` file transfer protocol
`wget` another popular program for downloading content from web and ftp sites

## secure communication with remote hosts

`ssh` (secure shell)
- authetnicates that the remote host is who it says it is
- encrypts all of the communications between the local and remote hosts

an SSH server runs on a remote host, listening for incoming connections (by default on port 22).

An SSH client is used on the local system to communicate with the remote server.
