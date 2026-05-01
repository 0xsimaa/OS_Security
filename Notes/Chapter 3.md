
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
- Improves responsiveness and scalability.

### Multithreading Benefits

| Benefit              | Description                                                   |
| -------------------- | ------------------------------------------------------------- |
| **Responsiveness**   | Application continues even if part is blocked (especially UI) |
| **Resource Sharing** | Threads share address space → easier data sharing than IPC    |
| **Economy**          | Cheaper/faster to create and switch threads vs. processes     |
| **Scalability**      | Takes full advantage of multicore systems                     |

### Multicore Programming Challenges

- Dividing activities into parallel tasks
- **Balance**; equal work distribution
- **Data splitting**; divide data among tasks
- **Data dependency** – synchronization (recall producer-consumer)
- **Testing & debugging** is much harder in concurrent/parallel code

### Concurrency vs. Parallelism

- **Concurrency**: Multiple tasks make progress (even on single core via time-sharing)
- **Parallelism**: Multiple tasks execute **simultaneously** (requires multiple cores)

**Types of Parallelism**

- **Data Parallelism** (SIMD): Same operation on different data subsets
- **Task Parallelism** (MISD): Different operations on (possibly same) data

### User Threads vs. Kernel Threads

- **User threads**: Managed by user-level thread library (in user space)
- **Kernel threads**: Supported and managed directly by the OS kernel

### Multithreading Models

| Model            | Mapping                            | Pros                                 | Cons                                               | Used Today?  |
| ---------------- | ---------------------------------- | ------------------------------------ | -------------------------------------------------- | ------------ |
| **Many-to-One**  | Many user → 1 kernel thread        | Simple, low overhead                 | One thread blocks → all block; no true parallelism | Rarely       |
| **One-to-One**   | Each user thread → 1 kernel thread | True concurrency, better parallelism | Higher overhead; limited # of threads              | Very common  |
| **Many-to-Many** | Many user ↔ smaller # of kernel    | Best of both worlds                  | Complex to implement                               | Some systems |
| **Two-level**    | Many-to-Many + optional binding    | Flexible                             | Still complex                                      | Common       |

### Thread Libraries

A thread library provides an API for creating and managing threads.

#### Major Libraries
- **POSIX Pthreads** (most UNIX/Linux/Mac)
- **Windows Threads**