
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
- **Java Threads** (managed by JVM)

**Pthreads Example**

```C
#include <pthread.h>
pthread_t tid;
pthread_create(&tid, NULL, runner, argv[1]);   // create
pthread_join(tid, NULL);                       // wait

```

**Windows Threads Example**

```C
HANDLE ThreadHandle = CreateThread(NULL, 0, Summation, &Param, 0, &ThreadId);
WaitForSingleObject(ThreadHandle, INFINITE);
```

**Java Threads (Runnable interface)**

```Java
class Task implements Runnable {
    public void run() { /* code */ }
}
Thread worker = new Thread(new Task());
worker.start();
worker.join();
```

### Implicit Threading

Programmer specifies **tasks**, not threads. Compiler/runtime library handles threading.

#### Four Popular Approaches
- **Thread Pools**
	- Pre-create pool of threads that wait for work.
	- Faster than creating new threads; limits total threads.
- **Fork-Join Parallelism**
	- Main thread forks subtasks -> subtasks run in parallel -> join results.
	- Recursive divide-and-conquer style.
- **OpenMP** (C/C++/Fortran)

```C
#pragma omp parallel for
for (i = 0; i < N; i++) { c[i] = a[i] + b[i]; }
```

- Grand Central Dispatch (Apple – macOS/iOS)
	- Uses **blocks** (^{}) placed in dispatch queues.
	- Runtime manages thread pool automatically.

### Threading Issues

| Issue                          | Description                                                                        |
| ------------------------------ | ---------------------------------------------------------------------------------- |
| **fork() / exec() Semantics**  | `fork()` may duplicate only calling thread or all threads (UNIX variations)        |
| **Signal Handling**            | Where to deliver signal in multithreaded process? (per-thread, every thread, etc.) |
| **Thread Cancellation**        | Asynchronous (immediate) vs. Deferred (check at cancellation points)               |
| **Thread-Local Storage (TLS)** | Each thread gets its own copy of data (useful with thread pools)                   |
| **Scheduler Activations**      | Kernel → user library upcalls to maintain correct # of kernel threads              |

### Operating System Examples
#### Windows Threads
- One-to-one, kernel-level