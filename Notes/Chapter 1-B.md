### Chapter 1-B: Operating System Services & Structure

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
- **Resource Allocation** – CPU, memory, I/O devices
- **Logging** – Record system usage and events
- **Protection and Security** – Control access to resources (this is the core focus of our **OS_Security** repo)

**Key Diagram Insight**: All user programs and interfaces interact with the OS through **system calls**, which sit above the actual OS services layer.

### User and Operating System Interface 

The OS provides three main ways for users to interact with it:

#### Command Line Interface (CLI)
Allows direct command entry 
- Can be implemented in the kernel or as a system program 
- Multiple shells possible (e.g., Bourne Shell, Bash) 
- Commands can be built-in or external programs

**Example**: Bourne Shell (`sh`) in action — shows commands like `uptime`, `df -h`, `ps aux`, etc.

#### Graphical User Interface (GUI)
- User-friendly “desktop metaphor” 
- History: Xerox PARC (1970) → Xerox Alto (1973) → Apple Macintosh (1980) → Microsoft Windows (1985) 
- Most modern systems now offer **both** CLI and GUI 
- Windows: GUI + “Command Prompt”/PowerShell - macOS: Aqua GUI + UNIX shells 
- Linux: CLI + optional GUIs (GNOME, KDE, etc.)

#### Touchscreen Interface
- Designed for mobile/tablet devices 
- Gesture-based interaction (no mouse) 
- Virtual keyboard + voice commands

### System Calls

System calls are the **programming interface** to the OS services. They are the only way a user program can request services from the kernel.
- User programs usually call them via high-level **APIs** (not directly) 
- Common APIs: 
	- **Win32 API** (Windows) 
	- **POSIX API** (UNIX, Linux, macOS) 
	- **Java API** (JVM)

**Example**: Copying a file requires a whole sequence of system calls (open, read, write, close, etc.).

**Standard API Example**: (`read()` in UNIX/Linux):

**C sample code:**
```c
#include <unistd.h>
 ssize_t read(int fd, void *buf, size_t count);
```

#### API → System Call → OS Relationship
- User application calls API function (e.g., open())
- API forwards request to system call interface
- Kernel executes the actual system call and returns result

#### System Call Implementation
- The caller only follows the API format
- OS hides all internal details
- Return status and values are passed back through the API

#### System Call Parameter Passing (3 Methods)
- **Pass parameters in registers** (fast but limited number)
- **Parameters in a block/table in memory** (address passed in register) — used by Linux & Solaris
- Parameters pushed onto the stack (most flexible)

**Diagram Insight**: Block/Table method allows unlimited parameters.

### Types of System Calls

System calls are grouped into six major categories:

| Category                    | Examples (Windows)             | Examples (Unix/Linux)   |
| --------------------------- | ------------------------------ | ----------------------- |
| **Process Control**         | CreateProcess(), ExitProcess() | fork(), exit(), wait()  |
| **File Management**         | CreateFile(), ReadFile()       | open(), read(), write() |
| **Device Management**       | SetConsoleMode()               | ioctl(), read()         |
| **Information Maintenance** | GetCurrentProcessID()          | getpid(), alarm()       |
| **Communications**          | CreatePipe(), MapViewOfFile()  | pipe(), mmap()          |
| **Protection**              | SetFileSecurity()              | chmod(), chown()        |

### Standard C Library Example

```C
printf("Greetings");

```

→ C library intercepts it → calls write() system call → kernel handles it.

### System Services / Utilities

These are programs that provide a convenient environment for users and developers:
- File manipulation
- Status information
- Programming language support
- Program loading & execution
- Communications
- Background services
- Application programs

Important: Most users only ever see system programs, not the raw system calls.

### Linkers and Loaders

**Linker:**
- Combines object files + libraries into a single executable
- Resolves external references

**Loader**:
- Brings the executable into memory for execution
- Modern OSes use **dynamic linking** (DLLs in Windows, shared libraries in Linux)

**Role Diagram Summary:**
> source.c → compiler → object.o → linker → executable → loader → program in memory