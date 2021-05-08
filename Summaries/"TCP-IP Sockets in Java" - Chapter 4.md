# Chapter 4: Beyond the Basics
## 4.1 Multitasking
### 4.1.1 Java Threads
Java provides two approaches for performing a task in a new thread: 1) defining a subclass of the Thread class with a run() method that performs the task, and instantiating it; or 2) defining a class that implements the Runnable interface with a run() method that performs the task, and passing an instance of that class to the Thread constructor. In either case, the new thread does not begin execution until its start() method is invoked. The first approach can only be used for classes that do not already extend some other class, the second approach is always applicable.
### 4.1.2 Server Protocol
Since the multitasking server approaches we are going to describe are independent of the particular client-server protocol, we want to be able to use the same protocol implementation for both. The code for the echo protocol is given in the class EchoProtocol. This class encapsulates the per-client processing in the static method handleEchoClient(). This code is almost identical to the connection-handling portion of TCPEchoServer.java, except that a logging capability (described shortly) has been added; the method takes references to the client Socket and the Logger instance as arguments.
### 4.1.3 Thread-per-Client
In a thread-per-client server, a new thread is created to handle each connection. The server executes a loop that runs forever, listening for connections on a specified port and repeatedly accepting an incoming connection from a client and then spawning a new thread to handle that connection.
### 4.1.4 Thread Pool
### 4.1.5 System-Managed Dispatching: The Executor Interface
## 4.2 Blocking and Timeouts
### 4.2.1 accept(), read(), and receive()
### 4.2.2 Connecting and Writing
### 4.2.3 Limiting Per-Client Time
## 4.3 Multiple Recipients
### 4.3.1 Broadcast
### 4.3.2 Multicast
## 4.4 Controlling Default Behaviors
### 4.4.1 Keep-Alive
### 4.4.2 Send and Receive Buffer Size
### 4.4.3 Timeout
### 4.4.4 Address Reuse
### 4.4.5 Eliminating Buffering Delay
### 4.4.6 Urgent Data
### 4.4.7 Lingering after Close
### 4.4.8 Broadcast Permission
### 4.4.9 Traffic Class
### 4.4.10 Performance-Based Protocol Selection
## 4.5 Closing Connections
## 4.6 Applets
