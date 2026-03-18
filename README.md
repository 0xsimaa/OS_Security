## OS_Security Notes (Defensive Approach)

Welcome to **OS_Security**! This repository is a complete archive of my university Operating Systems course materials. It contains well-organized lecture notes, solved assignments, quizzes, programming projects, midterm papers, and final exams covering all major topics: Operating Systems Fundamentals & Overview, Process Management, Threads and Concurrency, CPU Scheduling, Synchronization, Deadlocks, Memory Management, Storage Management, I/O Systems, File Systems, and **Security & Protection**.

> Whether you're reviewing core OS concepts or focusing on security and protection mechanisms, everything is neatly structured and ready to help students, self-learners, and enthusiasts master operating systems. Contributions, suggestions, and stars are always welcome! ⭐

---

### 1. Operating Systems Fundamentals & Overview

Introduction to the role and purpose of operating systems. Covers OS history and evolution, types of operating systems (batch, multiprogrammed, time-sharing, distributed, real-time, and mobile), system calls and services, OS structures (monolithic, layered, microkernel, hybrid, and exokernel), virtual machines, containers, the boot process, and system generation. This section builds the foundation for understanding how an OS acts as a bridge between hardware and user applications.

### 2. Process Management

Core concepts of processes — the basic unit of execution in an OS. Includes the process concept, process states, Process Control Block (PCB), process creation and termination, context switching, inter-process communication (IPC) using shared memory and message passing, client-server models, and process scheduling queues. Real-world examples from Linux (fork(), exec(), wait()) and Windows are provided with code snippets.

### 3. Threads and Concurrency

Exploration of threads as lightweight processes that enable efficient concurrency. Topics include thread models (user-level, kernel-level, and hybrid), multithreading benefits and challenges, thread libraries (POSIX Pthreads, Java threads, Windows threads), concurrency issues (race conditions, atomicity), and thread scheduling. Emphasis is placed on how threads improve performance in modern multi-core systems with practical coding examples.

### 4. CPU Scheduling

In-depth study of how the operating system decides which process or thread gets the CPU. Covers scheduling criteria (CPU utilization, throughput, turnaround time, waiting time, response time), basic algorithms (FCFS, SJF, Priority, Round-Robin), advanced algorithms (Multilevel Queue, Multilevel Feedback Queue), real-time scheduling, and scheduling in multi-processor environments. Includes Gantt chart visualizations and comparative performance analysis.

### 5. Synchronization

Mechanisms to coordinate concurrent processes and threads safely. Topics cover the critical-section problem, Peterson’s solution, hardware support (test-and-set, compare-and-swap), mutex locks, semaphores (binary and counting), monitors, and classic synchronization problems (Producer-Consumer, Readers-Writers, Dining Philosophers). Real implementations in Linux and Windows are demonstrated.

### 6. Deadlocks

Comprehensive coverage of deadlock situations and their resolution. Includes the four necessary conditions (mutual exclusion, hold-and-wait, no preemption, circular wait), resource-allocation graphs, deadlock prevention strategies, deadlock avoidance (Banker’s Algorithm with examples), deadlock detection algorithms, and recovery methods. Practical scenarios from real systems show how deadlocks occur and how to prevent them.

### 7. Memory Management

How the operating system manages main memory efficiently. Covers logical vs. physical address space, swapping, contiguous allocation, paging (page tables, TLB, multi-level paging), segmentation, virtual memory concepts, demand paging, page replacement algorithms (FIFO, Optimal, LRU, LFU), frame allocation, and thrashing with working-set model. Includes hands-on examples of address translation.

### 8. Storage Management

Management of secondary storage devices (mainly disks). Topics include disk structure and formatting, disk scheduling algorithms (FCFS, SSTF, SCAN, C-SCAN, LOOK), swap-space management, RAID levels for reliability and performance, boot block, bad-block handling, and overall storage device management. Focuses on improving I/O performance and reliability.

### 9. I/O Systems

Complete input/output management in operating systems. Covers I/O hardware (device controllers, buses), I/O software layers (user-level, device-independent, device-dependent, interrupt handlers), polling vs. interrupt-driven I/O, Direct Memory Access (DMA), I/O scheduling, buffering, caching, spooling, and error handling. Real examples from Linux device drivers are included.

### 10. File Systems

Design and implementation of file systems. Topics include file concept and attributes, directory structure (single-level, two-level, tree-structured), file access methods (sequential, direct, indexed), file allocation methods (contiguous, linked, indexed), free-space management (bit vector, linked list), mounting, file sharing, consistency semantics, and protection mechanisms. Practical implementations in ext4 (Linux) and NTFS (Windows) are discussed.

### 11. Security & Protection

Advanced protection and security mechanisms in operating systems (the main focus of this repository). Covers security threats and attacks, protection domains, access matrix, Access Control Lists (ACLs), capability lists, authentication and authorization, cryptography in OS (encryption, hashing), trusted operating systems, security models (Bell-LaPadula, Biba), mandatory vs. discretionary access control, common vulnerabilities (buffer overflows, privilege escalation), and modern security features (SELinux, AppArmor). Includes case studies and project work on implementing secure OS features.

---
