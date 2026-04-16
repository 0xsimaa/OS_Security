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