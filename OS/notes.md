<center>
<h1>Operating System</h1>
</center>

**Question 1:** What is an operating system?

**Answer:** An operating system is a program that acts as an interface between the user and the computer hardware and controls the execution of all kinds of programs.

**Question 2:** What are important functions of an operating system?

**Answer:** 
- Memory Management (File System)
- Process Management (Scheduling)
- Device Management (Drivers)
- Security (Password access and restricted access)
- Error Detection (Handling Deadlocks)

**Question 3:** Explain different types of operating systems.

**Answer:** 
1. Batch operating system
    - User prepares jobs offline and run it in system at one go
    - Lack of interaction between the user and the job.
    - CPU is often idle, because the speed of the mechanical I/O devices is slower than the CPU.
    - Difficult to provide the desired priority.
2. Multiprogramming operating system
    - A computer running more than one program at a time
3. Multiprocesing operating system
    - A computer using more than one CPU at a time.
4. Multitasking operating system
    - Tasks sharing a common resource (like 1 CPU).

**Question 4:** What is multithreading?

**Answer:** Multithreading is the ability of a central processing unit to provide multiple threads of execution concurrently, supported by the operating system.

**Question 5:** Disadvantages of Multithreading.

**Answer:** 
1. Can lead to deadlock
2. Difficult to debug
 
**Question 6:** Process vs Thread.

**Answer:**
- A process have its own code, data, heap and stack. Stack is required to manage function calls. Each thread has its own stack. 
- All threads in a process share code, data and heap of the process.
- Multiple threads can be running simultaneously on multiprocessor system.
- Threads in a same process share same address space.

**Question 7:** What are different process states?

**Answer:** 

![ProcessStates](https://i.ibb.co/6ZmvzQR/process-state.jpg)

- New and Suspend are in secondary memory
- Ready and waiting are in primary memory
- Running is in processor
 

**Question 8:** What is a process control block?

**Answer:** A process control block (PCB) is a data structure used by computer operating systems to store all the information about a process. It is also known as a process descriptor. When a process is created (initialized or installed), the operating system creates a corresponding process control block.

Its content vary from OS to OS, but few of the important ones are
- Process ID
- Process State
- CPU Register
- Accounts Information
- IO information
- CPU Scheduling Information
- Memory Information

**Question 9:** What is Process Scheduler.

**Answer:** Scheduler is a program which is responsible for loading, deleting and transfering processes between states in operating system.

There are 3 types of operating system
- **Long Term Scheduler -**  It brings the new process to the ‘Ready State’. It controls Degree of Multi-programming, i.e., number of process present in ready state at any point of time. It is important that the long-term scheduler make a careful selection of both IO and CPU bound process.  
- **Short Term Scheduler -** It is responsible for selecting one process from ready state for scheduling it on the running state.
- **Medium Term Scheduler -** It is responsible for suspending and resuming the process. It mainly does swapping (moving processes from main memory to disk and vice versa).

**Question 10:** What is a dispatcher?

**Answer:** Dispatcher is responsible for loading the process selected by Short-term scheduler on the CPU (Ready to Running State) Context switching is done by dispatcher only. 

A dispatcher does the following:
- Switching context.
- Switching to user mode.
- Jumping to the proper location in the newly loaded program.

**Question 11:** What is Job Queue and Ready Queue?

**Answer:**
- **Ready Queue:** All processes in ready queue.
- **Job Queue:** All programs which needs to be loaded on the primary memory to become ready/waiting.

**Question 12:** Advantages and Disadvantages of different scheduling algorithm.

**Answer:**
1. **First Come First Serve:**
    - **Advantages**
        - Simple Algorithm.
        - Every process will run, no starvation.
    - **Disadvantages:**
        - No option for pre-emption of a process.
        - Long waiting time.
2. **Shortest Job First:**
    - **Advantages**
        - Increased throughput.
        - Shorter process complete quickly.
    - **Disadvantages:**
        - Time taken by process must be known initially.
        - Longer processes may lead to starvation
3. **Shortest Remaining Time First:**
    - **Advantages**
        - Increased throughput.
        - Pre-emption is allowed.
    - **Disadvantages:**
        - Time taken by process must be known initially.
4. **Round Robin:**
    - **Advantages**
        - Equal priority among processes.
        - Starvation does not occur.
    - **Disadvantages:**
        - Big Quantum can lead to execution as FCFS.
        - If Quantum is short then context switching happens more often thus leads to inefficiency of processer.

**Question 13:** What is context switching?

**Answer:** Context Switching involves storing the context or state of a process so that it can be reloaded when required and execution can be resumed from the same point as earlier.

**Question 14:** What is race condition?

**Answer:** A race condition is an undesirable situation that occurs when a device or system attempts to perform two or more operations at the same time, but because of the nature of the device or system, the operations must be done in the proper sequence to be done correctly.
 
**Question 15:** What is critical section?

**Answer:** Snippets which causes race condition are known as critical section. 
 
**Question 16:** What is consumer-producer problem?

**Answer:**

Consider 2 snippets

```cpp
int itemCount = 0;
```
```cpp
 1. procedure producer(){
 2.     while (true){
 3.         item = produceItem();
 4.         if (itemCount == BUFFER_SIZE){
 5.             sleep();
 6.         }
 7.         putItemIntoBuffer(item);
 8.         itemCount = itemCount + 1;
 9.         if (itemCount == 1){
10.             wakeup(consumer);
11.         }
12.     }
13. }
```
```cpp
 1. procedure consumer() {
 2.     while (true) {
 3.         if (itemCount == 0){
 4.             sleep();
 5.         }
 6.         item = removeItemFromBuffer();
 7.         itemCount = itemCount - 1;
 8.         if (itemCount == BUFFER_SIZE - 1){
 9.             wakeup(producer);
10.         }
11.         consumeItem(item);
12.     }
13. }
```
What can happen is that there comes a higher priority process after line 7 of producer, thus not increasing itemCount but item is there in buffer. So if consumer is called, it will see it as 0 and sleep. This causes inconsistency.

**Question 17:** Goals of mutual exclusion?

**Answer:** 
1. Mutual Exclusion for resource must happen
2. Progress must happen
3. Bounded waiting for fair CPU usage
4. Performance should improve

**Question 18:** Methods of synchronisation.

**Answer:**
1. Disabling Interrupts.
2. Mutex (Locks)
3. Semaphore
4. Monitor
 

**Question 19:** What is a mutex?

**Answer:**  a mutex is locking mechanism used to synchronize access to a resource. Only one task (can be a thread or process based on OS abstraction) can acquire the mutex. It means there is ownership associated with mutex, and only the owner can release the lock (mutex).
 
**Question 20:** What is semaphore?

**Answer:**  Semaphore is simply a variable which is non-negative and shared between threads. This variable is used to solve the critical section problem and to achieve process synchronization in the multiprocessing environment.

- Semaphore is signaling mechanism (“I am done, you can carry on” kind of signal). For example, if you are listening songs (assume it as one task) on your mobile and at the same time your friend calls you, an interrupt is triggered upon which an interrupt service routine (ISR) signals the call processing task to wakeup.
- **Binary Semaphore:** This is also known as mutex lock. It can have only two values – 0 and 1
- **Counting Semaphore:** Its value can range over an unrestricted domain. It is used to control access to a resource that has multiple instances.
 
 

**Question 21:** What are monitors?

**Answer:** Monitors are classes which have synchronized functions. They are used in Java.
Example

```java
class Account{
    private int bal;
    void synchronize deposit(int x){
        bal=bal+x;
    }
    void synchronize credit(int x){
        bal=bal-x;
    }
}
```
 

**Question 22:** What is a deadlock?

**Answer:** Deadlock is a situation where a set of processes are blocked because each process is holding a resource and waiting for another resource acquired by some other process
 

**Question 23:** What are neccessary condition for deadlock?

**Answer:** There are 4 necessary condition for deadlock
1. **Mutual Exclusion-** If a resource is being used by one process, it cannot be used by another process.
2. **Hold and Wait-** Processes must be holding and waiting for some resource. If a process is not holding any resource or is not waiting for any resource then it cannot cause deadlock.
3. **No Preemption-** Operating system cannot take back allocated resources from the process
4. **Circular Wait-** Wait must be in circular order. Example
    - A holds P1 and waits for P2
    - B hold P2 and wait for P1
    
    So there is a circular wait A->P2->B->P1->A 

**Question 24:** What are methods of handling deadlock?

**Answer:** There are 4 methods to handle deadlock
1. **Prevent deadlock-** Do not let all 4 condition to possibly happen
2. **Avoid deadlock-** Do not grant a request which leads to deadlock
3. **Detect and Recover-** Detect Deadlock and recover
4. **Ignore it-** Interestingly it is used in Windows and Unix

**Question 25:** What is spooling?

**Answer:** SPOOL is an acronym for simultaneous peripheral operations on-line.  It is a kind of buffering mechanism or a process in which data is temporarily held to be used and executed by a device, program or the system. Data is sent to and stored in memory or other volatile storage until the program or computer requests it for execution.

In easier words, printer only prints one thing at a time. So what we can do is store future request in buffer and process them one by one. So whenever any processor asks for a printer in working state, it will be available and there is no mutual exclusion property for deadlock. This is called Spooling.
 
**Question 26:** How to prevent deadlock by making counter measures against hold and wait criteria?

**Answer:**
1. Ask process to declare its usage time (impractical)
2. Ask process to release all resources before making a new request
 
**Question 27:** Banker's algorithm for avoidance of deadlock and to even detect it.

**Answer:** Must Revise
 
**Question 28:**  

**Answer:**
 
**Question:** 

**Answer:**
 
**Question:** 

**Answer:**
 
**Question:** 

**Answer:**
 
**Question:** 

**Answer:**
 