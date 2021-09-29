# Introduction to Operating Systems
### Operating Systems
An operating system is a piece of software that manages all the resources of a computer system,
both hardware and software, and provides an environment in which the user can execute his
programs in a convenient and efficient manner.

### Functions of Operating Systems
- manages the computer hardware
- facilitates execution of application programs
- acts as an intermediary between the user and the computer hardware
- designed to be convenient and efficient

### Types of Operating Systems
1. Batch Operating Systems 
    - This type of operating system does not interact with the computer directly. There is an operator which takes similar jobs having the same requirement and group them into batches. It is the responsibility of the operator to sort jobs with similar needs.
    - Advantages
        - Processors of the batch systems know how long the job would be when it is in queue
        - Multiple users can share the batch systems
        - The idle time for the batch system is very less
        - It is easy to manage large work repeatedly in batch systems
    - Disadvantages
        - Operators should be well known with batch systems
        - Hard to debug
        - Costly
        - The other jobs will have to wait for an unknown time if any job fails
    - Example
        - Payroll System
        - Bank Statements
2. Time-Sharing Operating Systems
    - Each task is given some time to execute so that all the tasks work smoothly. Each user gets the time of CPU as they use a single system. These systems are also known as **Multitasking Systems**. The task can be from a single user or different users also. The time that each task gets to execute is called **quantum**. After this time interval is over OS switches over to the next task.
    - Advantages
        - Each task gets an equal opportunity
        - Quick response
        - Fewer chances of duplication of software
        - CPU idle time can be reduced 
    - Disadvantages
        - Reliability problem
        - Security and integrity of user programs and data
        - Data communication problem
    - Examples
        - Unix
        - Multics
3. Distributes Operating Systems
    - Various autonomous interconnected computers communicate with each other using a shared communication network. Independent systems possess their own memory unit and CPU. These are referred to as **loosely coupled systems** or distributed systems. These system’s processors differ in size and function. The major benefit of working with these types of the operating system is that it is always possible that one user can access the files or software which are not actually present on his system but some other system connected within this network i.e., remote access is enabled within the devices connected in that network. 
    - Advantages
        - Failure of one will not affect the other network communication, as all systems are independent from each other
        - Electronic mail increases the data exchange speed
        - Since resources are being shared, computation is highly fast and durable
        - Load on host computer reduces
        - These systems are easily scalable as many systems can be easily added to the network
        - Delay in data processing reduces
    - Disadvantages
        - Failure of the main network will stop the entire communication
        - To establish distributed systems the language which is used are not well defined yet
        - These types of systems are not readily available as they are very expensive. Not only that the underlying software is highly complex and not understood well yet
    - Examples
        - Locus
4. Network Operating Systems
    - These systems run on a server and provide the capability to manage data, users, groups, security, applications, and other networking functions. These types of operating systems allow shared access of files, printers, security, applications, and other networking functions over a small private network. One more important aspect of Network Operating Systems is that all the users are well aware of the underlying configuration, of all other users within the network, their individual connections, etc. and that’s why these computers are popularly known as **tightly coupled systems**. 
    - Advantages  
        - Highly stable centralized servers
        - Security concerns are handled through servers
        - New technologies and hardware up-gradation are easily integrated into the system
        - Server access is possible remotely from different locations and types of systems
    - Disadvantages 
        - Servers are costly
        - User has to depend on a central location for most operations
        - Maintenance and updates are required regularly
    - Examples
        - Microsoft Windows Server 2008
        - UNIX
        - Linux
        - Mac OS X
5. Real-Time Operating System
    - These types of OSs serve real-time systems. The time interval required to process and respond to inputs is very small. This time interval is called **response time**. 
    - Real-time systems are used when there are time requirements that are very strict like missile systems, air traffic control systems, robots, etc. 
    - Types of Real Time system
        1. Hard Real-Time Systems
            - These OSs are meant for applications where time constraints are very strict and even the shortest possible delay is not acceptable. 
            - These systems are built for saving life like automatic parachutes or airbags which are required to be readily available in case of any accident. 
            - Virtual memory is rarely found in these systems.
        2. Soft Real-Time Systems
            - These OSs are for applications where for time-constraint is less strict.
    - Advantages
        - Maximum Consumption: Maximum utilization of devices and system, thus more output from all the resources
        - Task Shifting: The time assigned for shifting tasks in these systems are very less. For example, in older systems, it takes about 10 microseconds in shifting one task to another, and in the latest systems, it takes 3 microseconds.
        - Focus on Application: Focus on running applications and less importance to applications which are in the queue.
        - Real-time operating system in the embedded system: Since the size of programs are small, RTOS can also be used in embedded systems like in transport and others.
        - Error Free: These types of systems are error-free.
        - Memory Allocation: Memory allocation is best managed in these types of systems.
    - Disadvantages
        - Limited Tasks: Very few tasks run at the same time and their concentration is very less on few applications to avoid errors.
        - Use heavy system resources: Sometimes the system resources are not so good and they are expensive as well.
        - Complex Algorithms: The algorithms are very complex and difficult for the designer to write on.
        - Device driver and interrupt signals: It needs specific device drivers and interrupts signals to respond earliest to interrupts.
        - Thread Priority: It is not good to set thread priority as these systems are very less prone to switching tasks.
    - Examples
        - weapon systems
        - robots
        - air traffic control systems
### Multiprogramming, multitasking, multithreading, multiprocessing
- Multiprogramming
    - All the programs(or **jobs**) are placed in a queue for execution (or **job pool**). The scheduler picks jobs one-by-one and executes till the time quantum expires, or the process is pre-emptied by some external factors (I/O requirement, interrupt, etc.). In such a case, the process is context-switched with the next one, thus preventing the CPU from being idle.
    - Multi programming occurs by switching from one process to other (phenomenon called as **context switching**)
- Multiprocessing
    - Use of two or more CPUs (processors) within a single Computer system.
    - Multiprocessing occurs by means of parallel processing
    - Advantages
        - Failure-tolerance. i.e. Even if one CPU fails, the system can keep running relying upon the other processors
        - Significant gains in computation by horizontally scaling the system (using multiple mediocre CPUs instead of upgrading the single one)
        - I/O and peripheral devices can be shared amongst the units thus saving total expense.
- Multitasking
    - Execution of multiple tasks (say processes, programs, threads etc.) at a time.
    - Multi programming works solely on the concept of context switching whereas multitasking is based on time sharing alongside the concept of context switching(Multiprogramming + time sharing)
- Multi threading
    - Thread
        - Basic unit of CPU utilization
        - Threads have common shared resources (memory, file descriptors, code segment, etc). However, it has independent stack-space, program-counters, etc.
        - Example
            - VLC media player, where one thread is used for opening the VLC media player, one thread for playing a particular song and another thread for adding new songs to the playlist
            - Tabs in chrome(each tab is a thread)
    - Multi threading is an execution model that allows a single process to have multiple code segments (i.e., threads) running concurrently within the “context” of that process.
    - Advantages
        - Increased responsiveness(no user is left idle)
        - Less cost

# Process Management
### Process
- A process(**job**) is a program in execution
- Process is an ‘active’ entity, while program is a ‘passive’ entity
- Example
    - When we write a program in C++ and compile it, the compiler creates binary code. The original code and binary code are both programs. When we actually run the binary code, it becomes a process

### Process States
![Process States 5 state model](/assets/OS/process_state_5_state_model.png) 
![Process States 7 state model](/assets/OS/process_state_7_state_model.png)
1. New (Create) 
    - Process is about to be created but not yet created
    - Program which is present in secondary memory that will be picked up by OS to create the process
2. Ready 
    - New -> Ready to run
    - After the creation of a process, the process enters the ready state i.e. the process is loaded into the main memory(RAM).
    - Process here is ready to run and is waiting to get the CPU time for its execution. Processes that are ready for execution by the CPU are maintained in a queue for ready processes
3. Run 
    - Process is chosen by CPU for execution and the instructions within the process are executed by anyone of the available CPU cores
4. Blocked or wait 
    - Whenever the process requests access to I/O or needs input from the user or needs access to a critical region(the lock for which is already acquired), it enters the blocked or waits for the state
    - The process continues to wait in the main memory and does not require CPU. Once the I/O operation is completed the process goes to the ready state
5. Terminated or completed 
    - Process is killed(deallocated) as well as PCB is deleted
6. Suspend ready 
    - Process that was initially in the ready state but were swapped out of main memory(refer Virtual Memory topic) and placed onto external storage by scheduler are said to be in suspending ready state. The process will transition back to ready state whenever the process is again brought onto the main memory. Linux uses swap space and partition to do this task
7. Suspend wait or suspend blocked 
    - Similar to suspend ready but uses the process which was performing I/O operation and lack of main memory caused them to move to secondary memory
    - When work is finished it may go to suspend ready

### Process Management - Process Scheduling
- CPU and IO Bound Processes 
    - If the process is intensive in terms of CPU operations then it is called the CPU bound process. If the process is intensive in terms of I/O operations then it is called IO bound process.
- Types of process scheduler
    1. Long Term or job scheduler 
        - It brings the new process to the 'Ready State'. 
        - It controls Degree of Multi-programming, i.e., number of process present in ready state at any point of time.
        - It is important that the long-term scheduler make a careful selection of both IO and CPU bound processes.
    2. Short term or CPU scheduler
        - It is responsible for selecting one process from ready state for scheduling it on the running state.
        - Short-term scheduler only selects the process to schedule it doesn't load the process on running.
        - **Dispatcher** is responsible for loading the process selected by Short-term scheduler on the CPU (Ready to Running State) Context switching is done by dispatcher only. A dispatcher does the following:
            - Switching context
            - Switching to user mode
            - Jumping to the proper location in the newly loaded program
    3. Medium-term scheduler 
        - It is responsible for suspending and resuming the process. It mainly does swapping (moving processes from main memory to disk and vice versa)
        - Swapping may be necessary to improve the process mix or because a change in memory requirements has overcommitted available memory, requiring memory to be freed up
- Multiprogramming 
    - We have many processes ready to run
    - Types of multiprogramming:
        1. Pre-emption (or time sharing or multitasking)
            - Process is forcefully removed from CPU
        2. Non pre-emption 
            - Processes are not removed until they complete the execution
- Degree of multiprogramming 
    - Number of processes that can reside in the ready state at maximum decides the degree of multiprogramming, e.g., if the degree of programming = 100 means 100 processes can reside in the ready state at maximum.
    - Types of queues of processes:
        1. Ready Queue
            - Set of all processes that are in main memory and are waiting for CPU time is kept in the ready queue.
        2. Job Queue
            - Each new process goes into the job queue. Processes in the job queue reside on mass storage and await the allocation of main memory.
        3. Waiting (Device) Queues
            - Set of processes waiting for allocation of certain I/O devices is kept in the waiting (device) queue
            - The short-term scheduler (also known as CPU scheduling) selects a process from the ready queue and yields control of the CPU to the process

### System Calls
- Modes of operation of OS
    1. Kernel Mode(OS)
        - Mode of operation in which critical OS procedures run. Only privileged instructions such as: Handling Interrupts, Process Management, I/O Management are allowed to run
        - This is to ensure that no user application is able to tamper or cause a glitch in core-OS tasks, thus preventing any critical error which may cause the system to crash
        - When OS boots, it begins execution in kernel-mode only. All user applications which are loaded afterwards are run on User Mode
    2. User Mode
        - All user applications and high-level programs are run in User Mode so that they don't mess up with the critical OS procedures
        - However, sometimes a user application may require access to low-level utilities such as I/O peripherals, File System (Hard-drives), etc. For that, it requires the OS to switch from the User Mode of execution to Kernel Mode. The way of switching is done via **System Calls**
        ![User Mode](/assets/OS/user_mode.jpeg)
- Types of system calls
    1. Process control: end, abort, create, terminate, allocate and free memory
    2. File management: create, open, read, write, delete file
    3. Device management: read, write console
    4. Information maintenance: getpid, alarm, sleep
    5. Communication: pipe
    6. Protection: chmod(set file security)
- fork
    - Fork system call is used to create a child process
    - It is a special function in the fact that this system call has a conditional return value:
        - -ve : Unsuccessful Child creation
        - 0: Value returned to the child process
        - +ve : Value returned to the parent process. It is equal to the PID (Process ID) of the child process
    - If we count the parent as 1 single processes, then after each fork call, 2 processes are said to exist now (the original parent and the newly created child).
    - Execution continues from the point of fork() call in both child and parent processes. i.e. The same code is executed in both the processes. However, everything else (variables, stack, heap etc.) is duplicated.(First parent executes and then child)
    - n fork() calls =>(makes) $2^n$ (process) = 1 (parent process) + $2^n$ - 1 (child process) 

### Thread
- Thread is a single sequence stream within a process
- Threads have same properties as of the process so they are called as **light weight processes**
- Threads are executed one after another but gives the illusion as if they are executing in parallel
- Each thread has different states. Each thread has
    - A program counter
    - A register set
    - A stack space
- Threads are not independent of each other as they share the code, data, OS resources, etc.
- Similarity between Threads and Processes -
    - Only one thread or process is active at a time
    - Within process both execute sequentially
    - Both can create children
- Differences between Threads and Processes -
    - Process have system calls involved, Threads don't have that
    - Threads are not independent, processes are
    - Threads are designed to assist each other, processes may or may not do it
    - Context switching: Faster in Thread, Slower in process
    - Blocking: If we block one process then other process aren't blocked but when we block one thread then all other threads are blocked as CPU blocks entire process
- Types of Threads
    1. User Level thread (ULT)
        - It is implemented in the user level library, they are not created using the system calls
        - Thread switching does not need to call OS and to cause an interrupt to Kernel. The kernel doesn't know about the user level thread and manages them as if they were single-threaded processes.
        - Advantages of ULT
            - Can be implemented on an OS that does't support multithreading.
            - Simple representation since thread has only program counter, register set, stack space.
            - Simple to create since no intervention of kernel
            - Thread switching is fast since no OS calls need to be made.
        - Disadvantages of ULT
            - If one thread causes a page fault, the entire process blocks.

    2. Kernel Level Thread (KLT)
        - Kernel knows and manages the threads. Instead of thread table in each process, the kernel itself has thread table (a master one) that keeps track of all the threads in the system. In addition kernel also maintains the traditional process table to keep track of the processes
        - OS kernel provides system call to create and manage threads.
        - Advantages of KLT -
            - Since kernel has full knowledge about the threads in the system, scheduler may decide to give more time to processes having large number of threads.
            - Good for applications that frequently block.
        - Disadvantages of KLT -
            - Slow and inefficient
            - It requires thread control block so it is an overhead

# Process Scheduling
### Types of time for CPU scheduling
1. Arrival Time
    - Time at which the process arrives in the ready queue
2. Completion Time
    - Time at which process completes its execution
3. Burst Time
    - Time required by a process for CPU execution
4. Turn Around Time
    - Turn Around Time = Completion Time - Arrival Time
5. Waiting Time(W.T)
    - Waiting Time = Turn Around Time - Burst Time
6. Response Time
    - Response Time = Time at which the process gets the CPU for the first time - Arrival time

### Scheduling Algorithms
1. First Come First Serve (FCFS)
    - Criteria: Minimum arrival time first
    - Mode: Non-Pre-emptive
    - FIFO(First in First Out) queue
    - Advantage:
        - Simple, easy to implement
    - Disadvantage:
        - Average waiting time not optimal
        - Convoy Effect - Whole OS slows down due to a few slow processes(due to FCFS)

    ![FCFS Question](/assets/OS/FCFS_Question.png)
    ![FCFS Grantt Chart](/assets/OS/FCFS_GranttChart.png)
    ![FCFS Answer](/assets/OS/FCFS_Answer.png)   
2. Shortest-Job-First (SJF)
    - Criteria: Minimum arrival time first and then burst time second in case of clash
    - Mode: Non-Pre-emptive
    - Advantage:
        - Minimum average waiting time
    - Disadvantage:
        - Starvation
        - Impractical as not possible to calculate burst time in advance

    ![SJF Question](/assets/OS/SJF_Question.png)
    ![SJF Grantt Chart](/assets/OS/SJF_GranttChart.png)
    ![SJF Answer](/assets/OS/SJF_Answer.png)
3. Shortest Remaining Time First (SRTF)
    - Criteria: Minimum arrival time first and then burst time second in case of clash(Burst Time)
    - Mode: Pre-emptive(Move only 1 unit of time and check)
    - Advantage:
        - Short processes are handled very quickly
        - Less overhead since it only makes a decision when a process completes or a new process is added
    - Disadvantage:
        - Starvation
        - Impractical since it is not possible to know the burst time of every process in ready queue in advance.

    ![SRTF Question](/assets/OS/SRTF_Question.png)
    ![SRTF Grantt Chart](/assets/OS/SRTF_GranttChart.png)
    ![SRTF Answer](/assets/OS/SRTF_Answer.png)

4. Round Robin Scheduling
    - Criteria: Time Quantum
    - Mode: Pre-emptive
    - Advantage: No need for calculating burst time
    - Disadvantage: Overhead due to context switching
    - Example: Following is solved for time quantum = 2, Make ready queue according to arrival time and then after completing a time quantum first put arrived process in ready queue and then put completed process(context switching after time quantum(except at end of last process and beginning of start process))

    ![Round Robin Question](/assets/OS/RoundRobin_Question.png)
    ![Round Robin Grantt Chart](/assets/OS/RoundRobin_GranttChart.png)
    ![Round Robin Answer](/assets/OS/RoundRobin_Answer.png)

5. Priority Scheduling
    - Criteria: Priority(Process with the highest priority is to be executed first and so on. Processes with the same priority are executed on the FCFS scheme)
    - Mode: Non-pre-emptive/Pre-emptive
    - A major problem with priority scheduling is indefinite blocking or **Starvation**. A solution to the problem of indefinite blockage of the low-priority process is **ageing**. Aging is a technique of gradually increasing the priority of processes that wait in the system for a long period of time
    - Example - For pre-emptive(Move only 1 unit of time and check)

    ![Priority Scheduling Question](/assets/OS/PriorityScheduling_Question.png)
    ![Priority Scheduling Grantt Chart](/assets/OS/PriorityScheduling_GranttChart.png)
    ![Priority Scheduling Answer](/assets/OS/PriorityScheduling_Answer.png)

6. Multilevel Queue Scheduling
    - System processes are of the highest priority (extremely critical), then comes Interactive(Foreground) processes followed by Batch(Background) and Student processes
    - Each process have different ready queue, scheduling algorithms, priority
    - Scheduling among queues
        1. **Fixed priority preemptive scheduling method** - Each queue has absolute priority over lower priority queue
        2. **Time slicing** - In this method each queue gets certain portion of CPU time and can use it to schedule its own processes
    - Disadvantage: Starvation

7. Multilevel Feedback Queue Scheduling
    - Modification to the MLQ (Multilevel-Queue) which allows processes to move between queues. It keeps analyzing the behavior (time of execution) of processes, according to which it changes its priority

# Process Synchronization
- Process synchronization problem arises in the case of Cooperative process also because resources are shared in Cooperative processes
### Types of Process(on basis of synchronization)
1. Independent Process
    - Execution of one process does not affect the execution of other processes
    - Each process have their own address space and they don't require to communicate with other processes
2. Cooperative Process
    - Execution of one process affects the execution of other processes
    - Resources are shared between process

### Race Condition
- Several processes access and process the manipulations over the same data concurrently, then the outcome depends on the particular order in which the access takes place

### Critical Condition
- It is a code segment that can be accessed by only one process at a time. It contains shared variables which need to be synchronized to maintain consistency of data variables.
- Parts of Critical Section
    - Entry Section
        - It is part of the process which decides the entry of a particular process in the Critical Section, out of many other processes
    - Exit Section
        - This process allows the other process that is waiting in the Entry Section, to enter into the Critical Sections. It checks that a process that after a process has finished execution in Critical Section can be removed through this Exit Section
    - Remainder Section
        - The other parts of the Code other than Entry Section, Critical Section and Exit Section is known as Remainder Section
- Conditions of synchronization
    1. Mutual Exclusion (Primary/Mandatory)
        - If a process is executing in its critical section, then no other process is allowed to execute in the critical section.
    2. Progress (Primary)
        - If no process is in its critical section, and if one or more threads want to execute their critical section then any one of these threads must be allowed to get into its critical section
    3. Bounded Waiting (Secondary)
        - After a process makes a request for getting into its critical section, there is a limit for how many other processes can get into their critical section, before this process's request is granted. So after the limit is reached, the system must grant the process permission to get into its critical section.
    4. Performance/Portability (Secondary)
        - The mechanism that allows only one process to enter the critical section should be fast. This mechanism is referred to as the locking mechanism and can be implemented in two ways, hardware or software mechanism. The hardware-based mechanism is generally faster since it only involves the registers.

### Solutions for Process Synchronization
1. Lock Variable
    - (LOCK = {0, 1} => 0 for if process not in critical section)
    - Executed in User Mode
    - Multiprocess Solution
    - No Mutual Exclusion 
    - ``` C++
        Entry section - while(lock != 0);
                        Lock = 1;
        //critical section
        Exit section - Lock = 0;```
2. Test and Set (Same as Lock variable) [Hardware Mode]
    - Here, the shared variable is lock which is initialized to false
    - TestAndSet(lock) algorithm 
        - It always returns whatever value is sent to it and sets lock to true. The first process will enter the critical section at once as TestAndSet(lock) will return false and it’ll break out of the while loop. The other processes cannot enter now as lock is set to true and so the while loop continues to be true. Mutual exclusion is ensured. Once the first process gets out of the critical section, lock is changed to false. So, now the other processes can enter one by one. Progress is also ensured. However, after the first process any process can go in. There is no queue maintained, so any new process that finds the lock to be false again, can enter. So bounded waiting is not ensured. 
    - ``` C++
        //Shared variable lock initialized to false
        boolean lock;

        boolean TestAndSet (boolean &target){
            boolean rv = target;
            target = true;
            return rv;
        }

        while(1){
            while (TestAndSet(lock));
            critical section
            lock = false;
            remainder section
        }
        ```
3. Turn Variable (Strict Alteration)
    - User Mode
    - Only for 2 processes
    - Same as lock but instead of 0 or 1 we use turn == pid of process then only process run
    - Mutual Exclusion is there
    - Progress not guaranteed
    - Bounded Waiting is there
    - Portability is there
4. Semaphore
    - Semaphore => Integer variable
    - Types of Semaphore
        1. Counting Semaphore
            - s can be any value (s = count of processes that can run at a time)
            - For multiple process
            - No mutual Exclusion
            - ``` C++
                // While entering critical condition -> wait, down, P
                void wait(int s) {
                    s--;
                    // No resource available
                    if(s < 0) {
                        // Add process to blocked queue and sleep
                    } 
                }
                // While exiting -> signal, up, V
                void signal(int s) {
                    s++;
                    if(s <= 0) {
                        // Remove from blocked
                    }
                }
                ```
        2. Binary Semaphore (Mutex Lock)
            - s can be 0 or 1 (initially 1)
            - The wait operation only works when the semaphore is 1 and the signal operation succeeds when semaphore is 0
            - Follows mutual exclusion
            - Portability is there
            - Busy waiting
### Producer Consumer problem (counting semaphore)
- Problem
    - We have a buffer of fixed size. A producer can produce an item and can place in the buffer. A consumer can pick items and can consume them
    - In this problem, buffer is the critical section
- Solution
    - We need two counting semaphores – Full and Empty. “Full” keeps track of number of items in the buffer at any given time and “Empty” keeps track of number of unoccupied slots
    - ``` C++
        // Initialization of semaphores
        mutex = 1
        Full = 0 // Initially, all slots are empty. Thus full slots are 0
        Empty = n // All slots are empty initially

        // Solution for Producer
        do{
            //produce an item
            wait(empty);
            wait(mutex);
            //place in buffer
            signal(mutex);
            signal(full);
        }while(true);

        // Solution for Consumer
        do{
            wait(full);
            wait(mutex);
            // remove item from buffer
            signal(mutex);
            signal(empty);
            // consumes item
        }while(true);
      ```

### Reader-Writer Problem (Binary Semaphore)
- Problem
    - In case when we can't change file/data while other person is reading or writing
    - Allowed -> R-R
    - Not allowed -> R-W, W-R, W-W
- Solution 
    - Binary Semaphore
    - ``` C++
        // Initialization
        semaphore mutex, wrt; // semaphore mutex is used to ensure mutual exclusion when readcnt is updated i.e. when any reader enters or exit from the critical section and semaphore wrt is used by both readers and writers
        int readcnt;  //    readcnt tells the number of processes performing read in the critical section, initially 0

        // Writer process
        do {
            // writer requests for critical section
            wait(wrt);  
            // performs the write
            // leaves the critical section
            signal(wrt);
        } while(true);

        // Reader process
        do {
            // Reader wants to enter the critical section
            wait(mutex);
            // The number of readers has now increased by 1
            readcnt++;                          
            // there is atleast one reader in the critical section
            // this ensure no writer can enter if there is even one reader
            // thus we give preference to readers here
            if (readcnt==1)     
                wait(wrt);                    
            // other readers can enter while this current reader is inside 
            // the critical section
            signal(mutex);                   
            // current reader performs reading here
            wait(mutex);   // a reader wants to leave
            readcnt--;
            // that is, no reader is left in the critical section,
            if (readcnt == 0) 
                signal(wrt);         // writers can enter
            signal(mutex); // reader leaves
        } while(true);
      ```

### Dining Philosopher Problem (Binary Semaphore)
- Problem 
    - K philosophers seated around a circular table with one chopstick between each pair of philosophers(total K chopsticks). There is one chopstick between each philosopher. A philosopher may eat if he can pick up the two chopsticks adjacent to him. One chopstick may be picked up by any one of its adjacent followers but not both
- Solution
    - ``` C++
        // Initialize semaphore
        semaphore chopstick [K];
        // Initially the elements of the chopstick are initialized to 1 as the chopsticks are on the table and not picked up by a philosopher

        // Structure of a philosopher i
        do {
            wait( chopstick[i] );
            wait( chopstick[ (i+1) % K] );
            . .
            . EATING THE RICE
            .
            signal( chopstick[i] );
            signal( chopstick[ (i+1) % K] );
            .
            . THINKING
            .
        } while(1);
      ```
    - Problem -> Deadlock => If all philosophers pick their left chopstick simultaneously. Then none of them can eat and deadlock occurs.
    - Solve
        - At most (K - 1) philosophers at table [Not appropriate]
        - Even philosopher should pick right chopstick, and then left chopstick while an odd philosopher should pick left chopstick and then right chopstick
        - A philosopher should only be allowed to pick their chopstick if both are available at the same time

# Deadlock
- Situation where a set of processes are blocked because each process is holding a resource and waiting for another resource acquired by some other process
- Example

    ![Deadlock Example](/assets/OS/deadlock_example.png)
### Conditions for deadlock(Necessary conditions)
1. Mutual Exclusion: One or more than one resource are non-sharable (Only one process can use at a time)
2. Hold and Wait: A process is holding at least one resource and waiting for resources
3. No Preemption: A resource cannot be taken from a process unless the process releases the resource
4. Circular Wait: A set of processes are waiting for each other in circular form.
### Resource Allocation Graph (RAG)
- It gives us what is the state of the system in terms of processes and resources
- Components of RAG
    1. Vertex
    ![RAG Vertex](/assets/OS/RAG_vertex.jpeg)
    2. Edge
    ![RAG Edge](/assets/OS/RAG_edge.jpeg)
### Cases of Deadlock
1. Single Resource Instance
    - Cycle in single-instance resource type is the sufficient condition for deadlock
    ![Deadlock in Single Resource Instance Example 1](/assets/OS/deadlock_singleResourceInstance_Example1.jpeg)
    ![Deadlock in Single Resource Instance Example 2](/assets/OS/deadlock_singleResourceInstance_Example2.jpeg)
2. Multiple Resource Instance
    - Construct Allocation and Request Matrix
    - Example 1
        ![Deadlock in Multiple Resource Instance Example 1 RAG](/assets/OS/deadlock_multipleResourceInstance_Example1_RAG.jpeg)
        ![Deadlock in Multiple Resource Instance Example 1 Matrix](/assets/OS/deadlock_multipleResourceInstance_Example1_Matrix.jpeg)
        - Allocation matrix
            - For constructing allocation matrix, just go to resources and see to which process it is allocated
            - R1 is allocated to P1, therefore write 1 in allocation matrix and similarly, R2 is allocated to P2 as well as P3 and for the remaining element just write 0
        - Request matrix
            - In order to find out request matrix, you have to go to process and see outgoing edges
            - P1 is requesting resource R2, so write 1 in matrix and similarly, P2 requesting R1 and for remaining element write 0
        - So now available resource is = (0, 0)
        - Checking deadlock (safe or not)
            ![Deadlock in Multiple Resource Instance Example 1 Checking Deadlock](/assets/OS/deadlock_multipleResourceInstance_Example1_CheckingDeadlock.jpeg)
        - So, there is no deadlock in this RAG. Even though there is a cycle, still there is no deadlock. Therefore in multi-instance resource cycle is not sufficient condition for deadlock
    - Example 2
        ![Deadlock in Multiple Resource Instance Example 2 RAG](/assets/OS/deadlock_multipleResourceInstance_Example2_RAG.jpeg)
        ![Deadlock in Multiple Resource Instance Example 2 Matrix](/assets/OS/deadlock_multipleResourceInstance_Example2_Matrix.jpeg)
        - So, Available resource is = (0, 0), but requirement are (0, 1), (1, 0) and (1, 0).So you can't fulfill any one requirement.Therefore, it is in deadlock

### Deadlock Handling
1. Deadlock Ignorance (Ostrich Method)
    - If the deadlock is very rare, then let it happen and reboot the system. This is the approach that both Windows and UNIX take.
2. Deadlock Detection and Recovery
    - Let deadlock occur, then do preemption to handle it once occurred
3. Deadlock Prevention
    - OS accepts all sent requests. Idea is to not to send a request that might lead to a deadlock condition
    - Can be done after avoiding any condition of deadlock
        1. No Mutual Exclusion 
            - Not possible to do it as some resource like printer are always non-shareable
        2. Preemption 
            - Preempt resources from process when resources required by other high priority processes
        3. No Hold and Wait 
            - Allocate all required resources to the process before the start of its execution, this way hold and wait condition is eliminated but it will lead to low device utilization
            - Process will make a new request for resources after releasing the current set of resources. This solution may lead to starvation
        4. No circular wait
            - Each resource will be assigned with a numerical number. A process can request resources only in increasing order of numbering
4. Deadlock Avoidance
    - OS very carefully accepts requests and checks whether if any request can cause deadlock and if process leads to deadlock, the process is avoided
    - ***Banker's Algorithm***
        - Used for deadlock avoidance and detection
        - Data Structures used
            - Available- A vector of length m indicates number of available resources of each type
            - Allocation- An n*m matrix defines number of resources of each type currently allocated to a process. Column represents resource and resource represent process.
            - Request- An n*m matrix indicates the current request of each process. If request[i][j] equals k then process Pi is requesting k more instances of resource type Rj
        - Steps of Algorithm
            1. Let Work and Finish be vectors of length m and n respectively. Initialize Work=Available. For i=0, 1, ...., n-1, if Allocation[i] = 0, then Finish[i] = true; otherwise, Finish[i]= false.
            2. Find an index i such that both
            a) Finish[i] == false b) Request[i] <= Work If no such i exists go to step 4.
            3. Work= Work+ Allocation[i] Finish[i]= true Go to Step 2.
            4. If Finish[i]== false for some i, 0<=i<n, then the system is in a deadlocked state. Moreover, if Finish[i]==false the process Pi is deadlocked.
        - Example

            ![deadlock Banker's Algorithm Question](/assets/OS/deadlock_Banker'sAlgorithm_Question.png)
            ![deadlock Banker's Algorithm Need](/assets/OS/deadlock_Banker'sAlgorithm_Need.png)
            ![deadlock Banker's Algorithm Safe state](/assets/OS/deadlock_Banker'sAlgorithm_SafeState.png)

# Memory Management

### Memory Mangement Techniques
![Memory Management Techniuqes](/assets/OS/memoryManagement_techniques.png)
- Static or Fixed Partitioning Technique (Contiguous)
    - In this partitioning, a number of partitions (non-overlapping) in RAM is fixed but the size of each partition may or may not be same. Here partition is made before execution or during system configure
    - Types of Static Technique
        1. Equal Size Memory Allocation: In this technique, fixed memory size is allocated to each process
        2. Unequal Size Memory allocation: This technique is used to reduce memory loss in comparison to the equal size memory allocation
    - Fragmentation
        - Occurs in a dynamic memory allocation system when many of the free blocks are too small to satisfy any request
        - Types of Fragmentation 
            1. External Fragmentation: External Fragmentation happens when a dynamic memory allocation algorithm allocates some memory and a small piece is left over that cannot be effectively used. If too much external fragmentation occurs, the amount of usable memory is drastically reduced. Total memory space exists to satisfy a request, but it is not contiguous.
            2. Internal Fragmentation: Internal fragmentation is the space wasted inside of allocated memory blocks because of restriction on the allowed sizes of allocated blocks. Allocated memory may be slightly larger than requested memory; this size difference is memory internal to a partition, but not being used.
    - Advantages of Fixed Partitioning
        1. Easy to implement
        2. Little OS overhead
    - Disadvantages of Fixed Partitioning
        1. Internal Fragmentation
        2. External Fragmentation
        3. Limit process size: Process of size greater than size of partition in Main Memory cannot be accommodated
        4. Limitation on Degree of Multiprogramming: Number of processes greater than number of partitions in RAM is invalid in Fixed Partitioning.
    
- Dynamic or Variable Partitioning Technique (Contiguous)
    - Initially RAM is empty and partitions are made during the run-time according to process's need instead of partitioning during system configure
    - Advantages of Variable Partitioning
        1. No Internal Fragmentation
        2. No restriction on Degree of Multiprogramming
        3. No Limitation on the size of the process
    - Disadvantages of Variable Partitioning
        1. Difficult Implementation
        2. External Fragmentation: If two non continuous process like P1(4 MB), P3(5 MB) is completed and a new process of 8 MB comes then this can not be used as in this only contiguous allocation is possible. These spaces are called ***holes***

### Partition Allocation Techniques (Contiguous)
1. First Fit (Fast)
    - Partition is allocated which is first sufficient block from the top of Main Memory
2. Next Fit (Fast)
    - Next fit is similar to the first fit but it will search for the first sufficient partition from the last allocation point
3. Best Fit (Slow)
    - Allocate the process to the partition which is the first smallest sufficient partition among the free available partition
4. Worst Fit (Slow)
    - Allocate the process to the partition which is the largest sufficient among the freely available partitions available in the main memory

### Paging
- Paging is a storage mechanism that allows OS to retrieve processes from the secondary storage into the main memory in the form of pages. In the Paging method, the main memory is divided into small fixed-size blocks of physical memory, which is called frames. The size of a frame should be kept the same as that of a page to have maximum utilization of the main memory and to avoid external fragmentation. 
- Paging is used for faster access to data
- Non-Contiguous
- Translating Logical Address To Physical Address
    - Logical Address
        - Address generated by CPU
        - Parts of logical Address
            - ***Page Number*** specifies specific page of process from which CPU wants to read data
            - ***Page Offset*** specifies the specific word on the page that CPU wants to read
    - Page Table 
        - Provides corresponding frame number (base address of the frame) where that page is stored in the main memory
    - Physical Address 
        - Physical location of required data in a memory
        - Parts 
            - ***Frame number*** specifies specific frame where required page is stored
            - ***Page Offset*** specifies specific word that has to be read from that page
- Advantages
    - No external fragmentation
- Disadvantages
    - Internal fragmentation
    - There is an overhead of maintaining a page table for each process
![Page Table Entries](/assets/OS/paging_pageTableEntries.png)

### Virtual Memory Management - Thrashing
- Condition or a situation when system is spending major portion of its time in servicing page faults(occurs when a program attempts to access data or code that is in its address space, but is not currently located in system RAM), but the actual processing done is very negligible
![Thrashing](/assets/OS/memoryManagement_Thrashing.png)

### Segmentation
- The chunks that a program(process) is divided into which are not necessarily all of the same sizes are called segments. Segmentation gives the user's view of the process that paging does not give
- Segment Table
    - Base Address: It contains the starting physical address where the segments reside in memory
    - Limit: It specifies the length of the segment
- Advantages
    - No Internal fragmentation.
    - Segment Table consumes less space in comparison to Page table in paging
- Disadvantages
    - As processes are loaded and removed from the memory, the free memory space is broken into little pieces, causing External fragmentation

### Overlay
- The process of transferring a block of program code or other data into internal memory, replacing what is already stored
- Advantages
    - Time, Memory Efficient
- Disadvantages
    - Complex
    - Must be specified by programmer
    - Programmer should know memory requirement

### Virtual Memory Management
- A computer can address more memory than the amount physically installed on the system. This extra memory is actually called virtual memory and it is a section of a hard disk that's set up to emulate the computer's RAM

### Translation Lookaside Buffer (TLB)
- Cache (Stores most recently used entries of page table)
- Effective memory access time (EMAT)
    - TLB is used to reduce effective memory access time as it is a high speed associative cache.
    - EMAT = h*(c+m) + (1-h)*(c+2m)
    where, h = hit ratio of TLB (Hit means present in TLB)
    m = Memory access time
    c = TLB access time
    here no page fault occur

### Page replacement Algorithm
- Since actual physical memory is much smaller than virtual memory, page faults happen. In case of a page fault, the Operating System might have to replace one of the existing pages with the newly needed page. Different page replacement algorithms suggest different ways to decide which page to replace. The target for all algorithms is to reduce the number of page faults.
1. First In First Out (FIFO)
![Page Replacement Algorithm FIFO](/assets/OS/memoryManagement_PageReplacementAlgorithm_FIFO.png)