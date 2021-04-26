# Chapter 1: Basic Sockets
## 2.1 Socket Addresses
- The InetAddress abstraction represents a network destination, encapsulating both names and numerical address information. The class has two subclasses, Inet4Address and Inet6Address.
- To get the addresses of the local host, the program takes advantage of the Network Interface abstraction.
## 2.2 TCP Sockets
- Java provides two classes for TCP: Socket and ServerSocket.
- Servers handle both ServerSocket and Socket instances, while clients use only Socket.
### 2.2.1 TCP Client
- The client initiates communication with a server that is passively waiting to be contacted. The
typical TCP client goes through three steps:
  - Construct an instance of Socket.
  - Communicate using the socket’s I/O streams.
  - Close the connection using the close() method of Socket.
### 2.2.2 TCP Server
- 
### 2.2.3 Input and Output Streams
- 
## 2.3 UDP Sockets
### 2.3.1 DatagramPacket
- 
### 2.3.2 UDP Client
- 
### 2.3.3 UDP Server
- 
### 2.3.4 Sending and Receiving UDP Sockets
- 
