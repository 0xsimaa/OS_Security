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

---

## 4. Computer System Organization

A computer system consists of:

- One or more CPUs
- Main memory
- Device controllers (for I/O devices)
- A system bus connecting all components    

A key concept here is **concurrency**:

- CPU and I/O devices can operate simultaneously
- Multiple processes may compete for resources

The OS manages this competition to prevent conflicts and inefficiency.

---

## 5. System Boot Process

When a computer starts, it does not immediately load the OS.

Instead:

1. A **bootstrap program** (firmware) runs first    
2. It initializes hardware components
3. It loads the OS kernel into memory
4. Execution of the OS begins    

This bootstrap program is stored in ROM/EPROM and is essential for system startup.

---

## 6. Interrupts

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

---

## 7. I/O System Structure

Each I/O device is controlled by a **device controller**, which has:

- Local buffers    
- Control and data registers

The OS interacts with devices through **device drivers**, which act as an abstraction layer.

### I/O Methods:

1. **Programmed I/O (Polling)**  
    CPU repeatedly checks device status (inefficient)
2. **Interrupt-driven I/O**  
    Device notifies CPU when ready (more efficient)
3. **Direct Memory Access (DMA)**
    - Device transfers data directly to memory
    - CPU involvement is minimal
    - Only one interrupt per data block
    - Used in high-speed devices