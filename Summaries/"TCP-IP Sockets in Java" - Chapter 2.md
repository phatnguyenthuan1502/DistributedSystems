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
  1. Construct an instance of Socket.
  2. Communicate using the socket’s I/O streams.
  3. Close the connection using the close() method of Socket.
### 2.2.2 TCP Server
- The server’s job is to set up a communication endpoint and passively wait for connections from clients. The typical TCP server goes through two steps:
  1. Construct a ServerSocket instance, specifying the local port. This socket listens for incoming connections to the specified port. 
  2. Repeatedly:
      - Call the accept() method of ServerSocket to get the next incoming client connection. Upon establishment of a new client connection, an instance of Socket for the new connection is created and returned by accept().
      - Communicate with the client using the returned Socket’s InputStream and OutputStream.
      - When finished, close the new client socket connection using the close() method of Socket.
### 2.2.3 Input and Output Streams
- OutputStream is the abstract superclass of all output streams in Java. Using an OutputStream, we can write bytes to, flush, and close the output stream.
- InputStream is the abstract superclass of all input streams. Using an InputStream, we can read bytes from and close the input stream.
## 2.3 UDP Sockets
- UDP performs only two functions: 1) it adds another layer of addressing to that of IP, and 2) it detects some forms of data corruption that may occur in transit and discards any corrupted messages.
- UDP sockets do not have to be connected before being used.
- UDP sockets preserve message boundaries.
- Java programmers use UDP sockets via the classes DatagramPacket and DatagramSocket. Both clients and servers use DatagramSockets to send and receive DatagramPackets.
### 2.3.1 DatagramPacket
- UDP endpoints exchange self-contained messages, called datagrams, which are represented in Java as instances of DatagramPacket.
- In addition to the data, each instance of DatagramPacket also contains address and port information.
### 2.3.2 UDP Client
- A UDP client begins by sending a datagram to a server that is passively waiting to be contacted. The typical UDP client goes through three steps:
  1. Construct an instance of DatagramSocket, optionally specifying the local address and port.
  2. Communicate by sending and receiving instances of DatagramPacket using the send() and receive() methods of DatagramSocket.
  3. When finished, deallocate the socket using the close() method of DatagramSocket.
### 2.3.3 UDP Server
- 
### 2.3.4 Sending and Receiving UDP Sockets
- 
