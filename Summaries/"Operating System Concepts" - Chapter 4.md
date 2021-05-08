# Chapter 4: Threads and Concurrency
## 4.1 Overview
- A thread represents a basic unit of CPU utilization, and threads belonging to the same process share many of the process resources, including code and data.
- There are four primary benefits to multithreaded applications:
1. Responsiveness: Multithreading an interactive application may allow a program to continue running even if part of it is blocked or is performing a lengthy operation, thereby increasing responsiveness to the user.
2. Resource sharing: Processes can share resources only through techniques such as shared memory and message passing.
3. Economy: Because threads share the resources of the process to which they belong, it is more economical to create and context-switch threads. Additionally, context switching is typically faster between threads than between processes.
4. Scalability: The benefits of multithreading can be even greater in a multiprocessor architecture, where threads may be running in parallel on different processing cores.
## 4.2 Multicore Programming
### 4.2.1 Programming Challenges

### 4.2.2 Types of Parallelism

## 4.3 Multithreading Models
### 4.3.1 Many-to-One Model

### 4.3.2 One-to-One Model

### 4.3.3 Many-to-Many Model

## 4.4 Thread Libraries
### 4.4.1 Pthreads

### 4.4.2 Windows Threads

### 4.4.3 Java Threads

## 4.5 Implicit Threading
### 4.5.1 Thread Pools

### 4.5.2 Fork Join

### 4.5.3 OpenMP

### 4.5.4 Grand Central Dispatch

### 4.5.5 Intel Thread Building Blocks

## 4.6 Threading Issues
### 4.6.1 The fork() and exec() System Calls

### 4.6.2 Signal Handling

### 4.6.3 Thread Cancellation

### 4.6.4 Thread-Local Storage

### 4.6.5 Scheduler Activations

## 4.7 Operating-System Examples
### 4.7.1 Windows Threads

### 4.7.2 Linux Threads
