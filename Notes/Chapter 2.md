### Chapter 2: Processes
---
### Process Concept
- **Process** = A **program in execution**.
- A program is a passive entity stored on disk; it becomes an active process when loaded into memory.
- Execution is **sequential** (no parallel execution of a single process’s instructions).
- Multiple processes can run **concurrently** on a system.

#### Parts of a Process in Memory
| Section   | Contains                                                                |
| --------- | ----------------------------------------------------------------------- |
| **Text**  | Program code (executable instructions)                                  |
| **Data**  | Global variables                                                        |
| **Heap**  | Dynamically allocated memory at runtime                                 |
| **Stack** | Temporary data (function parameters, local variables, return addresses) |
- The **program counter (PC)** and CPU registers represent the **current state** of the process.

#### Process States
As a process executes, it moves through the following states:
- **New** → Process is being created
- **Ready** → Waiting to be assigned to a processor
- **Running** → Instructions are being executed
- **Waiting** → Waiting for an event (I/O completion, signal, etc.)
- **Terminated** → Execution finished

#### Process Control Block (PCB)
The OS maintains a **Process Control Block (PCB)** (also called Task Control Block) for every process.

**Contents of PCB:**
- Process state (New, Ready, Running, etc.)
- Program counter
- CPU registers
- CPU scheduling information (priority, scheduling queue pointers)
- Memory-management information
- Accounting information (CPU time used, time limits)
- I/O status information (open files, devices allocated)

**Linux Representation:** *task_struct* (C structure)

### Process Scheduling
- **Scheduler** selects which process runs next on the CPU.
- Goal: Maximize CPU utilization and minimize response time.

**Scheduling Queues**
- **Ready Queue** – Processes in memory, ready to run
- **Wait Queue** (Device/ Event Queue) – Processes waiting for I/O or events
- Processes continuously migrate between queues

**Types of Schedulers**

| Scheduler                      | Purpose                                  | Frequency       | Key Responsibility                  |
| ------------------------------ | ---------------------------------------- | --------------- | ----------------------------------- |
| **Short-term** (CPU Scheduler) | Selects next process to run on CPU       | Milliseconds    | Fast, invoked very frequently       |
| **Long-term** (Job Scheduler)  | Decides which processes enter the system | Seconds/Minutes | Controls degree of multiprogramming |
| **Medium-term**                | Swapping (remove/re-introduce processes) | As needed       | Reduces degree of multiprogramming  |
- **I/O-bound** processes: Many short CPU bursts, spend more time doing I/O.
- **CPU-bound** processes: Few very long CPU bursts.

**Context Switch**
- Occurs when CPU switches from one process to another.
- OS saves the **context** (PCB) of the old process and loads the new one.
- Pure **overhead** – no useful work during switch.
- Time depends on hardware support.

### Operations on Processes

#### Process Creation
- **Parent** process creates **child** processes → forms a **process tree**.
- **UNIX/Linux:**
	- fork() → creates a duplicate child process.
	- exec() → replaces child’s memory space with a new program.
	- wait() → parent waits for child to terminate.