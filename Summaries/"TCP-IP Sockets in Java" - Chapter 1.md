# Chapter 1: Introduction
## 1.1 Networks, Packets, and Protocols
- A computer network consists of machines interconnected by communication channels (hosts and routers). A communication channel is a means of conveying sequences of bytes from one host to another.
- A few hosts connect to a router, which connects to other routers, and so on to form the network. This arrangement lets each machine get by with a relatively small number of communication channels. Programs that exchange information over the network do not interact directly with routers.
- Packets are sequences of bytes that are constructed and interpreted by programs. A packet contains control information that the network uses to do its job and sometimes also includes user data. Routers use such control information to figure out how to forward each packet.
- A protocol is an agreement about the packets exchanged by communicating programs and what they mean. A protocol tells how packets are structured.
- TCP/IP is the suite of protocols used in the Internet, but it can be used in stand-alone private networks as well.
- TCP/IP and all other protocol suites are organized into layers. Such implementations typically reside in the operating system of a host. Applications access the services provided by UDP and TCP through the sockets API.
- In TCP/IP, the bottom layer consists of the underlying communication channels. Those channels are used by the network layer, which deals with the problem of forwarding packets toward their destination (i.e., what routers do). The single network layer protocol in the TCP/IP suite is the Internet Protocol.
- The Internet Protocol provides a datagram service: every packet is handled and delivered by the network independently. To make this work, each IP packet has to contain the address of its destination.
- The layer above IP is called the transport layer. It offers a choice between two protocols: TCP and UDP. Each builds on the service provided by IP, but they do so in different ways to provide different kinds of transport, which are used by application protocols with different needs.
- TCP is designed to detect and recover from the losses, duplications, and other errors. UDP, on the other hand, does not attempt to recover from errors experienced by IP.
# 1.2 About Addresses
- Internet addresses are binary numbers. They come in two types: version 4 (IPv4, 32 bits long) and version 6 (IPv6, 128 bits long).
## 1.3 About Names
## 1.4 Clients and Servers
## 1.5 What Is a Socket?
