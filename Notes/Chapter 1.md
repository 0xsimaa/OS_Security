### Why Study Operating Systems?

Operating systems are the foundation of all computing systems. Every application you use—whether it’s a browser, game, or cybersecurity tool—runs on top of an OS.

From a cybersecurity perspective, this becomes even more important because:

- Most attacks target OS-level vulnerabilities
- OS controls access to hardware and system resources
- Weak OS understanding leads to inefficient and insecure code

In short, if you understand the OS, you understand how the system actually behaves underneath your code.

### What is an Operating System?

An Operating System (OS) is a software layer that sits between the user and the hardware.

Instead of directly interacting with hardware (which is complex and unsafe), users and programs interact with the OS.

### Core Objectives:

- Execute user programs efficiently
- Simplify problem-solving for users
- Manage hardware resources effectively

You can think of the OS as both a **manager** and a **mediator**.

### Perspectives of an Operating System

### User Perspective:

From the user's point of view, the OS should:

- Be easy to use
- Provide fast response time
- Offer a smooth experience

Users generally do not care about how resources are managed internally.

### System Perspective:

From the system’s point of view, the OS acts as:

- A **resource allocator** (CPU, memory, I/O devices)
- A **control program** (ensures processes run correctly without conflicts)    

The OS must balance fairness, efficiency, and performance.

### Computer System Organization

A computer system consists of:

- One or more CPUs
- Main memory
- Device controllers (for I/O devices)
- A system bus connecting all components    

A key concept here is **concurrency**:

- CPU and I/O devices can operate simultaneously
- Multiple processes may compete for resources

The OS manages this competition to prevent conflicts and inefficiency.

### System Boot Process

When a computer starts, it does not immediately load the OS.

Instead:

1. A **bootstrap program** (firmware) runs first    
2. It initializes hardware components
3. It loads the OS kernel into memory
4. Execution of the OS begins    

This bootstrap program is stored in ROM/EPROM and is essential for system startup.

### Interrupts

Interrupts are a central concept in operating systems.

An interrupt is a signal sent to the CPU indicating that an event needs immediate attention.

### How Interrupts Work:

1. CPU pauses current execution
2. Control is transferred to an **Interrupt Service Routine (ISR)**
3. ISR handles the event
4. CPU resumes previous task

### Key Points:

- Interrupts are managed using an **interrupt vector**
- OS must save and restore CPU state during interrupts
- Modern OS are **interrupt-driven**, meaning they rely heavily on this mechanism

### I/O System Structure

Each I/O device is controlled by a **device controller**, which has:

- Local buffers    
- Control and data registers

The OS interacts with devices through **device drivers**, which act as an abstraction layer.

#### I/O Methods:

1. **Programmed I/O (Polling)**  
    CPU repeatedly checks device status (inefficient)
2. **Interrupt-driven I/O**  
    Device notifies CPU when ready (more efficient)
3. **Direct Memory Access (DMA)**
    - Device transfers data directly to memory
    - CPU involvement is minimal
    - Only one interrupt per data block
    - Used in high-speed devices

### Storage Structure

### Main Memory:

- Directly accessible by CPU
- Fast but volatile
- Typically RAM (DRAM)

### Secondary Storage:

- Non-volatile
- Used for long-term storage
- Examples: HDD, SSD

### Storage Hierarchy

Storage is organized based on:

- Speed    
- Cost
- Capacity

Faster storage:

- More expensive
- Smaller in size

Slower storage:

- Cheaper
- Larger capacity

### Caching:

Frequently used data is stored in faster storage (cache) to improve performance.  
This introduces complexity in maintaining data consistency.

### Multiprogramming and Multitasking

### Multiprogramming:

- Multiple jobs are kept in memory
- CPU switches when one job is waiting (e.g., for I/O)
- Improves CPU utilization

### Multitasking (Time-sharing):

- CPU switches rapidly between processes
- Provides interactive computing
- Users feel as if tasks run simultaneously

This requires efficient scheduling and memory management.

### Dual Mode Operation

To protect the system, OS operates in two modes:

- **User Mode**: Limited access
- **Kernel Mode**: Full access to hardware

### Important Concepts:

- Mode switching occurs via **system calls**
- Some instructions are **privileged** and only allowed in kernel mode

This prevents user programs from directly accessing critical resources.

### Process Management

A **process** is a program in execution.

### Key Differences:

- Program → passive
- Process → active

### OS Responsibilities:

- Create and terminate processes
- Schedule execution
- Handle synchronization and communication
- Manage deadlocks

### Types:

- Single-threaded (one execution flow)
- Multi-threaded (multiple execution flows)

### Memory Management

For a program to execute:

- Instructions must be in memory
- Data must be available in memory

### OS Responsibilities:

- Track memory usage
- Allocate and deallocate memory
- Move processes in and out of memory

Efficient memory management directly impacts system performance.

### File System Management

The OS provides a structured way to store and access data.

### Responsibilities:

- Create/delete files and directories
- Provide access control
- Map logical files to physical storage

The OS hides hardware complexity and provides a simple interface for users.

### Mass Storage Management

Handles long-term storage using disks.

### Key Functions:

- Mounting and unmounting drives    
- Managing free space
- Allocating storage
- Ensuring protection

Disk performance significantly affects overall system performance.

### Protection and Security

### Protection:

Controls access to system resources.

### Security:

Defends against attacks such as:

- Malware
- Denial of Service (DoS)
- Unauthorized access

### Key Mechanisms:

- User IDs and Group IDs
- Access control policies
- Privilege escalation management

### Virtualization

Virtualization allows multiple operating systems to run on a single physical machine.

### Concepts:

- **Emulation**: Different CPU architecture (slow)
- **Virtualization**: Same architecture (efficient)

A **Virtual Machine Manager (VMM)** handles virtual environments.

### Computing Environments

Modern systems operate in various environments:

- Traditional systems (PCs)
- Mobile systems (smartphones)
- Client-server systems
- Peer-to-peer systems
- Cloud computing environments
- Real-time embedded systems

Each environment has different OS requirements.

### Cloud Computing

Cloud computing provides computing resources over the internet.

### Types:

- Public cloud
- Private cloud
- Hybrid cloud

### Service Models:

- SaaS (Software as a Service)
- PaaS (Platform as a Service)
- IaaS (Infrastructure as a Service)

Cloud systems rely heavily on virtualization.

### Real-Time Embedded Systems

These systems operate under strict time constraints.

### Key Characteristics:

- Time-critical operations
- Limited functionality
- Used in IoT, industrial systems, and automation

Correctness depends on meeting timing deadlines.

### Open Source Operating Systems

Open-source OS provide access to source code.

### Examples:

- Linux
- BSD UNIX

### Benefits:

- Transparency
- Learning opportunity
- Customization
- Community-driven development

---
