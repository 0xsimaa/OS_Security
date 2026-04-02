### Chapter 2: Operating System Services & Structure

**Why Study Operating System Services & Structure?** Understanding how an operating system is built and what services it provides is critical, especially in cybersecurity.

- Most vulnerabilities and attacks (privilege escalation, rootkits, buffer overflows) happen at the OS service and structure level. 
- System calls and protection mechanisms are the **first line of defense** between user programs and hardware. 
- Knowing OS structure helps you write secure code, detect anomalies, and understand how modern defenses (SELinux, AppArmor, sandboxing) actually work.

In short, this chapter shows **how** the OS actually delivers the services we rely on every day and how it protects the system.

### Operating System Services

An operating system provides two main categories of services:

#### 1. Services Helpful to the Users

These make the system convenient and easy to use:
- **User Interface** 
	- Command Line Interface (CLI) / Command Interpreter 
	- Graphical User Interface (GUI) - Batch interface (shell scripts)
- **Program Execution** – Load and run programs
- **I/O Operations** – Read/write to devices
- **File-System Manipulation** – Create, delete, read, write files
- **Communications** 
	- Message passing 
	- Shared memory
- **Error Detection** – Handle and report hardware/software errors

#### 2. Services for Efficient Operation (System Perspective)

These ensure the OS runs smoothly and securely: