# Operating System Notes

## What is an Operating System?  
An **Operating System (OS)** is a piece of software that manages all the resources of a computer system — both hardware and software. It provides an environment in which users can execute programs efficiently by:  
- Hiding the underlying complexity of hardware.  
- Acting as a **resource manager**.  
- Serving as an **interface between user and hardware**.  
- Offering **platform support** for running multiple programs.  
- Ensuring **isolation, security, and protection**.  

---

## Key Roles of an Operating System  
- **Interface** → Connects user and hardware.  
- **Resource Manager** → Manages CPU, memory, storage, and I/O devices.  
- **Program Execution** → Provides a platform to run applications.  
- **Isolation & Protection** → Ensures processes don’t interfere with each other.  

---

## Types of Operating Systems  

### 1. Single-Process OS  
- Executes **one process at a time** until completion.  
- **Example:** MS-DOS  

---

### 2. Batch Processing OS  
- Groups processes into batches and executes them one by one.  
- Reduces manual intervention.  
- **Example:** ATLAS  

---

### 3. Multiprogramming OS  
- Executes one process at a time, but when a process waits for I/O, the CPU is reassigned to another process from the **task queue**.  
- Achieved using **context switching**.  
- **Example:** THE  

> **Note:**  
> - **PCB (Process Control Block):** A data structure that stores all information related to a process (process state, program counter, registers, etc.).  

---

### 4. Multitasking OS  
- Allows a single CPU to handle multiple tasks by **time-sharing**.  
- Creates an illusion that all programs run **simultaneously**.  

---

### 5. Multiprocessing OS  
- Supports **multiple CPUs (processors)** within a system.  
- Tasks are executed **in parallel** to improve performance.  
- Different from multitasking (where only one CPU switches between tasks).  

---

### 6. Distributed OS  
- Manages a **network of independent computers** and makes them appear as a **single unified system** to the user.  

---

### 7. Real-Time OS (RTOS)  
- Designed for **real-time applications** where correctness depends not only on the output but also on the **time it is produced**.  
- Offers **low error chances**, **predictability**, and **high computation speed**.  

---

## ✅ Summary  
The Operating System is the backbone of computer systems, managing hardware, providing a user interface, and enabling efficient execution of processes through various models like single-process, batch, multiprogramming, multitasking, multiprocessing, distributed, and real-time systems.  

# Process, Thread, and Multithreading

## Process  
- A **process** is a **program under execution**.  
- It has its own memory space, resources, and state.  

---

## Thread (Lightweight Process)  
- A **thread** is the **smallest unit of execution** within a process.  
- Represents a **sub-task** of a process that can run independently.  
- Multiple threads within the same process **share resources** (memory, files, etc.).  

---

## Multithreading  
- A process is divided into smaller independent **threads** that can execute **in parallel**.  
- Enhances efficiency by utilizing multiple CPUs.  
- Threads within a process run concurrently while sharing the same resources.  

**Example:**  
In a **text editor**:  
- Spell checking  
- Text formatting  
- Auto-saving  
…all are done by **separate threads** running simultaneously.  

---

## Difference Between Thread Switching and Context Switching  

### 🔹 Short Answer  
- **Thread Switching:** Faster, happens within the same process, as threads share resources.  
- **Context Switching:** Slower, happens between different processes, requires saving and loading full process state.  

---

### 🔹 Detailed Answer  

| Aspect | **Thread Switching** | **Context Switching** |
|--------|----------------------|------------------------|
| **Definition** | Switching between threads of the same process. | Switching between two independent processes. |
| **Overhead** | Very low → threads share memory/resources, so minimal state needs saving. | High → full process state (registers, memory map, PCB) must be saved/restored. |
| **Speed** | Faster | Slower |
| **Memory Use** | Threads share the same address space → less memory required. | Each process has its own memory space → more memory required. |
| **Resource Sharing** | Threads share code, data, and OS resources. | Processes do not share memory/resources directly. |
| **Use Case** | Multithreading inside an application (e.g., web browser tabs, text editor). | Running multiple applications (e.g., browser + media player). |

---

## ✅ Summary  
- **Process:** Program in execution.  
- **Thread:** Lightweight sub-task of a process.  
- **Multithreading:** Improves efficiency by parallel execution of threads.  
- **Thread Switching vs. Context Switching:** Thread switching is faster and lighter, while context switching is heavier and used for switching between independent processes.  

