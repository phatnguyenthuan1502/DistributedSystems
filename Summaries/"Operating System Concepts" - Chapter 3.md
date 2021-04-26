Chapter 3: Processes
1.	Process Concept
	The Process
o	A process is a program in execution
o	The memory layout of a process is typically divided into multiple sections:
	Text section
	Data Section
	Heap Section
	Stack Section
o	The sizes of the text and data sections are fixed. The stack and heap sections can shrink and grow dynamically during program execution.
	Process State
o	As a process executes, it changes state. A process may be in one of the following states:
	New
	Running
	Waiting
	Ready
	Terminated
	Process Control Block
o	Process Control Block  is the kernel data structure that represents a process in an operating system.
o	It contains many pieces of information associated with a specific process, including these:
	Process state
	Program counter
	CPU registers
	CPU-scheduling information
	Memory-management information
	Accounting information
	I/O status information
2.	Process Scheduling
	Scheduling Queues
o	As processes enter the system, they are put into a ready queue, where they are ready and waiting to execute on a CPU’s core. This queue is generally stored as a linked list.
o	Processes that are waiting for a certain event to occur placed in a wait queue.
	CPU Scheduling
o	The role of the CPU scheduler is to select from among the processes that are in the ready queue and allocate a CPU core to one of them.
o	Swapping is an intermediate form of scheduling, where a process is removed from memory and thus reduce the degree of multiprogramming. Later, the process can be reintroduced into memory, and its execution can be continued where it left off.
	Context Switch
o	An operating system performs a context switch when it switches from running one process to running another.
o	Context-switch times are highly dependent on hardware support.

3.	Operations on Processes
	Process Creation
o	The fork() and CreateProcess() system calls are used to create processes on UNIX and Windows systems, respectively.
	Process Termination
o	A process terminates when it finishes executing its final statement and asks the operating system to delete it by using the exit() system call.
4.	Interprocess Communication
o	Cooperating processes require an interprocess communication (IPC) mechanism that will allow them to exchange data. 
o	There are two fundamental models of interprocess communication: shared memory and message passing.
5.	IPC in Shared-Memory Systems
o	Interprocess communication using shared memory requires communicating processes to establish a region of shared memory.
o	Must have a buffer. Two types of buffers can be used: the unbounded buffer and the bounded buffer.
6.	IPC in Message-Passing Systems
o	If processes P and Q want to communicate, a communication link must exist between them. There are several methods for logically implementing a link and the send()/receive() operations:
	Direct or indirect communication 
	Synchronous or asynchronous communication
	Automatic or explicit buffering
7.	Examples of IPC Systems
	POSIX Shared Memory
	Mach Message Passing
	Windows
	Pipes

8.	Communication in Client – Server Systems
	Sockets
o	Sockets allow two processes on different machines to communicate over a network.
	Remote Procedure Calls
o	RPCs abstract the concept of function (procedure) calls in such a way that a function can be invoked on another process that may reside on a separate computer.

