
### Thread Definition

-  **Thread** = Basic unit of CPU utilization
	- “The basic unit of CPU utilization” (Silberschatz)
	- “A dispatchable unit of work” (Stallings)
	- “An independent flow of control” (IBM)
- Previously, a **process** meant a single thread of execution.
- Most modern applications are **multithreaded**.

### Motivation for Threads

- Multiple tasks within an application can run as separate threads:
	- Update display
	- Fetch data
	- Spell checking
	- Answer network requests
- **Process creation** is heavy-weight; **thread creation** is light-weight.
- Threads simplify code and improve efficiency.
- Kernels themselves are generally multithreaded.

### Single vs. Multithreaded Processes

| Aspect                   | Single-Threaded Process | Multithreaded Process                          |
| ------------------------ | ----------------------- | ---------------------------------------------- |
| **Code, Data, Files**    | Shared                  | Shared                                         |
| **Registers, PC, Stack** | One set per process     | Separate set **per thread**                    |
| **Memory Layout**        | One stack + heap        | Multiple stacks (one per thread) + shared heap |

### Multithreaded Server Architecture

- Client sends request → Server creates a new thread to handle it → Server resumes listening for more requests.