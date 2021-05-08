# Chapter 4: Threads and Concurrency
## 4.1 Overview
- A thread represents a basic unit of CPU utilization, and threads belonging to the same process share many of the process resources, including code and data.
- There are four primary benefits to multithreaded applications:
  - Responsiveness: Multithreading an interactive application may allow a program to continue running even if part of it is blocked or is performing a lengthy operation, thereby increasing responsiveness to the user.
  - Resource sharing: Processes can share resources only through techniques such as shared memory and message passing.
  - Economy: Because threads share the resources of the process to which they belong, it is more economical to create and context-switch threads. Additionally, context switching is typically faster between threads than between processes.
  - Scalability: The benefits of multithreading can be even greater in a multiprocessor architecture, where threads may be running in parallel on different processing cores.
## 4.2 Multicore Programming
### 4.2.1 Programming Challenges
- In general, five areas present challenges in programming for multicore
systems:
  - Identifying tasks: This involves examining applications to find areas that can be divided into separate, concurrent tasks.
  - Balance: While identifying tasks that can run in parallel, programmers must also ensure that the tasks perform equal work of equal value.
  - Data splitting: Just as applications are divided into separate tasks, the data accessed and manipulated by the tasks must be divided to run on separate cores.
  - Data dependency: The data accessed by the tasks must be examined for dependencies between two or more tasks.
  - Testing and debugging
### 4.2.2 Types of Parallelism
- Data parallelism focuses on distributing subsets of the same data across multiple computing cores and performing the same operation on each core.
- Task parallelism involves distributing not data but tasks (threads) across multiple computing cores. Each thread is performing a unique operation. Different threads may be operating on the same data, or they may be operating on different data.
## 4.3 Multithreading Models
### 4.3.1 Many-to-One Model
The many-to-one model maps many user-level threads to one kernel thread. Thread management is done by the thread library in user space. However, the entire process will block if a thread makes a blocking system call. Also, because only one thread can access the kernel at a time, multiple threads are unable to run in parallel on multicore systems.
### 4.3.2 One-to-One Model
The one-to-one model maps each user thread to a kernel thread. It provides more concurrency than the many-to-one model by allowing another thread to run when a thread makes a blocking system call. It also allows multiple threads to run in parallel on multiprocessors. The only drawback to this model is that creating a user thread requires creating the corresponding kernel thread, and a large number of kernel threads may burden the performance of a system.
### 4.3.3 Many-to-Many Model
The many-to-many model multiplexes many user-level threads to a smaller or equal number of kernel threads. The number of kernel threads may be specific to either a particular application or a particular machine. Developers can create as many user threads as necessary, and the corresponding kernel threads can run in parallel on a multiprocessor. Also, when a thread performs a blocking system call, the kernel can schedule another thread for execution.
## 4.4 Thread Libraries
A thread library provides an API for creating and managing threads. Three common thread libraries include Windows, Pthreads, and Java threading. Windows is for the Windows system only, while Pthreads is available for POSIX-compatible systems such as UNIX, Linux, and macOS. Java threads will run on any system that supports a Java virtual machine.
## 4.5 Implicit Threading
### 4.5.1 Thread Pools
The general idea behind a thread pool is to create a number of threads at start-up and place them into a pool, where they sit and wait for work. When a server receives a request, rather than creating a thread, it instead submits the request to the thread pool and resumes waiting for additional requests. If there is an available thread in the pool, it is awakened, and the request is serviced immediately. If the pool contains no available thread, the task is queued until one becomes free. Once a thread completes its service, it returns to the pool and awaits more work.
### 4.5.2 Fork Join
With this method, the main parent thread creates one or more child threads and then waits for the children to terminate and join with it, at which point it can retrieve and combine their results. For implicit threading, threads are not constructed directly during the fork stage; rather, parallel tasks
are designated. A library manages the number of threads that are created and is also responsible for assigning tasks to threads.
### 4.5.3 OpenMP
OpenMP identifies parallel regions as blocks of code that may run in parallel. Application developers insert compiler directives into their code at parallel regions, and these directives instruct the OpenMP run-time library to execute the region in parallel.
### 4.5.4 Grand Central Dispatch
GCD schedules tasks for run-time execution by placing them on a dispatch queue. When it removes a task from a queue, it assigns the task to an available thread from a pool of threads that it manages. GCD identifies two types of dispatch queues: serial and concurrent.
### 4.5.5 Intel Thread Building Blocks
Intel threading building blocks (TBB) is a template library that supports designing parallel applications in C++. As this is a library, it requires no special compiler or language support. Developers specify tasks that can run in par-allel, and the TBB task scheduler maps these tasks onto underlying threads. Furthermore, the task scheduler provides load balancing and is cache aware, meaning that it will give precedence to tasks that likely have their data stored in cache memory and thus will execute more quickly.
## 4.6 Threading Issues
- The fork() and exec() System Calls
- Signal Handling
- Thread Cancellation
- Thread-Local Storage
- Scheduler Activations
