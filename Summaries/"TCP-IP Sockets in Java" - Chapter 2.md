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
- Each datagram can be sent to or received from a different destination.
- The UDP echo client sends a datagram containing the string to be echoed and prints whatever it receives back from the server. A UDP echo server simply sends each datagram that it receives back to the client.
- Datagrams can be lost. To avoid this problem, use the setSoTimeout() method of DatagramSocket to specify a maximum amount of time to block on receive(), so it can try again by resending the echo request datagram.
### 2.3.3 UDP Server
-  UDP communication is initiated by a datagram from the client. The typical UDP server goes through three steps:
  1. Construct an instance of DatagramSocket, specifying the local port and, optionally, the local address.
  2. Receive an instance of DatagramPacket using the receive() method of DatagramSocket. When receive() returns, the datagram contains the client’s address so we know where to send the reply.
  3.  Communicate by sending and receiving DatagramPackets using the send() and receive() methods of DatagramSocket.
### 2.3.4 Sending and Receiving UDP Sockets
- UDP does not provide recovery from network errors and, therefore, does not buffer data for possible retransmission. This means that by the time a call to send() returns, the message has been passed to the underlying channel for transmission and is on its way out.
- A UDP socket’s received data is kept in a queue of messages, each with associated information identifying its source. A call to receive() will never return more than one message. However, if receive() is called with a DatagramPacket containing a buffer of size n, and the size of the first message in the receive queue exceeds n, only the first n bytes of the message are returned. The remaining bytes are quietly discarded, with no indication to the receiving program that information has been lost.
- The getData() method of DatagramPacket always returns the entire original buffer, ignoring the internal offset and length values. Receiving a message into the DatagramPacket only modifies those locations of the buffer into which message data was placed.
