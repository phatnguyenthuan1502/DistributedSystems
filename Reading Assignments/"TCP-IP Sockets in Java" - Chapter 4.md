# Chapter 4: Beyond the Basics
## 4.1 Multitasking
### 4.1.1 Java Threads
Java provides two approaches for performing a task in a new thread: 1) defining a subclass of the Thread class with a run() method that performs the task, and instantiating it; or 2) defining a class that implements the Runnable interface with a run() method that performs the task, and passing an instance of that class to the Thread constructor. In either case, the new thread does not begin execution until its start() method is invoked. The first approach can only be used for classes that do not already extend some other class, the second approach is always applicable.
### 4.1.2 Server Protocol
Since the multitasking server approaches we are going to describe are independent of the particular client-server protocol, we want to be able to use the same protocol implementation for both. The code for the echo protocol is given in the class EchoProtocol. This class encapsulates the per-client processing in the static method handleEchoClient(). This code is almost identical to the connection-handling portion of TCPEchoServer.java, except that a logging capability (described shortly) has been added; the method takes references to the client Socket and the Logger instance as arguments.
### 4.1.3 Thread-per-Client
In a thread-per-client server, a new thread is created to handle each connection. The server executes a loop that runs forever, listening for connections on a specified port and repeatedly accepting an incoming connection from a client and then spawning a new thread to handle that connection.
### 4.1.4 Thread Pool
The server creates a thread pool on start-up by spawning a fixed number of threads. When a new client connection arrives at the server, it is assigned to a thread from the pool. When the thread finishes with the client, it returns to the pool, ready to handle another request. Connection requests that arrive when all threads in the pool are busy are queued to be serviced by the next available thread.
### 4.1.5 System-Managed Dispatching: The Executor Interface
The interface Executor represents an object that executes Runnable instances according to some strategy, which may include details about queueing and scheduling, or how jobs are selected for execution.
## 4.2 Blocking and Timeouts
### 4.2.1 accept(), read(), and receive()
For these methods, we can set a bound on the maximum time (in milliseconds) to block, using the setSoTimeout() method of Socket, ServerSocket, and DatagramSocket. If the specified time elapses before the method returns, an InterruptedIOException is thrown. For Socket instances, we can also use the available() method of the socket’s InputStream to check for available data before calling read().
### 4.2.2 Connecting and Writing
- The Socket constructor attempts to establish a connection to the host and port supplied as arguments, blocking until either the connection is established or a system-imposed timeout occurs. Unfortunately, the system-imposed timeout is long, and Java does not provide any means of shortening it. To fix this, call the parameterless constructor for Socket, which returns an unconnected instance. To establish a connection, call the connect() method on the newly constructed socket and specify both a remote endpoint and timeout (milliseconds).
- A write() call blocks until the last byte written is copied into the TCP implementation’s local buffer; if the available buffer space is smaller than the size of the write, some data must be successfully transferred to the other end of the connection before the call to write() will return. Thus, the amount of time that a write() may block is ultimately controlled by the receiving application.
### 4.2.3 Limiting Per-Client Time
Suppose we want to implement the Echo protocol with a limit on the amount of time taken
to service each client. The protocol instance keeps track of the amount of time remaining, and uses setSoTimeout() to ensure that no read() call blocks for longer than that time.
## 4.3 Multiple Recipients
### 4.3.1 Broadcast
With broadcast, all hosts on the (local) network receive a copy of the message.
### 4.3.2 Multicast
With multicast, the message is sent to a multicast address, and the network delivers it only to those hosts that have indicated that they want to receive messages sent to that address.
## 4.4 Controlling Default Behaviors
### 4.4.1 Keep-Alive
- TCP provides a keep-alive mechanism where, after a certain time of inactivity, a probe message is sent to the other endpoint. If the endpoint is alive and well, it sends an acknowledgment. After a few retries without acknowledgment, the probe sender gives up and closes the socket, eliciting an exception on the next attempted I/O operation.
- By default, keep-alive is disabled. Call the setKeepAlive() method with true to enable keep-alive.
### 4.4.2 Send and Receive Buffer Size
- The getReceiveBufferSize(), setReceiveBufferSize(), getSendBufferSize(), and setSendBufferSize() methods get and set the size (bytes) of the receive and send buffers.
- The getReceiveBufferSize() and setReceiveBufferSize() methods get and set the size (bytes) of the receive buffer for Socket instances created by the accept().
### 4.4.3 Timeout
- We can specify a maximum blocking time for the various operations.
- The getSoTimeout() and setSoTimeout() methods get and set the maximum time (milliseconds) to allow read/receive and accept operations to block. A timeout of 0 means the operation never times out. If the timeout expires, an exception is thrown.
### 4.4.4 Address Reuse
- Under some circumstances, you may want to allow multiple sockets to bind to the same socket address. To enable this, you must allow address reuse.
- The getReuseAddress() and setReuseAddress() methods get and set reuse address permissions. A value of true means that address reuse is enabled.
### 4.4.5 Eliminating Buffering Delay
- TCP attempts to help you avoid sending small packets, which waste network resources. It does this by buffering data until it has more to send. While this is good for the network, your application may not be so tolerant of this buffering delay. You can disable this behavior.
- The getTcpNoDelay() and setTcpNoDelay() methods get and set the elimination of buffering delay. A value of true means that buffering delay is disabled.
### 4.4.6 Urgent Data
- TCP includes the concept of urgent data that can (theoretically) skip ahead. Such data is called out-of-band because it bypasses the normal stream.
- To send urgent data, call the sendUrgentData() method, which sends the least significant byte of the int parameter. To receive this byte, the receiver must enable out-of-band data by passing true to setOOBInline(). The byte is received in the input stream of the receiver.
### 4.4.7 Lingering after Close
- When you call close() on a socket, it immediately returns even if the socket is buffering unsent data. The problem is that your host could then fail at a later time without sending all of the data. You may optionally ask close() to “linger,” or block, by blocking until all of the data is sent and acked or a timeout expires.
- If you call setSoLinger() with on set to true, then a subsequent close() will block until all data is acknowledged by the remote endpoint or the specified timeout (seconds) expires. If the timeout expires, the TCP connection is forceably closed. The getSoLinger() method returns the timeout if linger is enabled and −1 otherwise.
### 4.4.8 Broadcast Permission
- DatagramSockets provide broadcast service.
- The getBroadcast() and setBroadcast() methods get and set broadcast permissions. A value of true means that broadcast is permitted. By default, Java permits broadcast.
### 4.4.9 Traffic Class
- Some networks offer enhanced or “premium” services to packets classified as being eligible for the service. The traffic class of a packet is indicated by a value carried in the packet as it is transmitted through the network.
- The traffic class is specified as an integer or a set of bit flags. The number and meaning of the bits depend on the version of IP you are using.
### 4.4.10 Performance-Based Protocol Selection
void setPerformancePreferences(int connectionTime, int latency, int bandwidth)
The performance preference for the socket is expressed by three integers representing connection time, delay, and bandwith.
## 4.5 Closing Connections
The shutdownInput() and shutdownOutput() methods of Socket allow the I/O streams to be closed independently. After shutdownInput(), the socket’s input stream can no longer be used. After shutdownOutput() is called on a Socket, no more data may be sent on the socket’s output stream.
## 4.6 Applets
Applets can perform network communication using TCP/IP sockets, but there are severe restrictions on how and with whom they can converse.
