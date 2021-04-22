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
- Internet addresses are binary numbers. There are two types: version 4 (IPv4, 32 bits long) and version 6 (IPv6, 128 bits long).
- IPv4 addresses are conventionally written as a group of four decimal numbers separated by periods (e.g., 10.1.2.3); this is called the dotted-quad notation. The four numbers in a dotted-quad string represent the contents of the four bytes of the Internet address.
- IPv6 address, on the other hand, are represented as groups of hexadecimal digits, separated by colons (e.g., 2000:fdb8:0000:0000:0001:00ab:853c:39a1). Each group of digits represents two bytes of the address leading zeros and consecutive groups that contain only zeros may be omitted.
- Technically, each Internet address refers to the connection between a host and an underlying communication channel: a network interface.
- The port number in TCP or UDP is always interpreted relative to an Internet address.
- The loopback address is always assigned to a special loopback interface, a virtual device that simply echoes transmitted packets right back to the sender.
- Private IPv4 addresses are often used in homes and small offices that are connected to the Internet through a network address translation (NAT) device. Such a device maps pairs in packets on one of its interfaces to pairs on the other interface. This enables a small group of hosts to effectively “share” a single IP address.
## 1.3 About Names
- The name-resolution service can access information from a wide variety of sources. Two of the primary sources are the Domain Name System (DNS) and local configuration databases.
- The DNS is a distributed database that maps domain names to Internet addresses and other information; the DNS protocol allows hosts connected to the Internet to retrieve information from that database using TCP or UDP. 
- Local configuration databases are generally OS-specific mechanisms for local name-to-Internet address mappings.
## 1.4 Clients and Servers
- The client program initiates communication, while the server program waits passively for and then responds to clients that contact it. Together, the client and server compose the application.
- The client needs to know the server’s address and port initially, but not vice versa. With the sockets API, the server can learn the client’s address information when it receives the initial communication from the client.
- Usually, the client knows the name of the server it wants and uses the name-resolution service to learn the corresponding Internet address.
- Servers can use any port, but the client must be able to learn what it is. A list of all the assigned port numbers is maintained by the numbering authority of the Internet.
## 1.5 What Is a Socket?
- A socket is an abstraction through which an application may send and receive data.
- Different types of sockets correspond to different underlying protocol suites and different stacks of protocols within a suite. The main types of sockets in TCP/IP today are stream sockets (uses TCP) and datagram sockets (uses UDP). 
- A TCP/IP socket is uniquely identified by an Internet address, an end-to-end protocol (TCP or UDP), and a port number.
