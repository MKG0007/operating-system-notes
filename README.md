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


# Components of Operating System

The Operating System is divided into **User Space** and **Kernel Space**, which interact to provide services and manage hardware efficiently.  

---

## 1. User Space  
- Runs **user applications** (apps, services).  
- **No direct hardware access**.  
- Interacts with the **kernel** for hardware operations.  
- Provides a convenient environment for applications via:  
  - **GUI (Graphical User Interface)** → user-friendly visuals.  
  - **CLI (Command Line Interface)** → text-based interaction.  

---

## 2. Kernel  
- Has **direct access** to hardware.  
- Core of the OS → manages system resources.  
- Interaction levels: **User Space → Kernel → Hardware**.  

### Functions of Kernel  
1. **Process Management**  
   - Process creation and termination.  
   - Process and thread scheduling.  
   - Process synchronization and inter-process communication (IPC).  

2. **Memory Management**  
   - Allocating and deallocating memory.  
   - Managing free space efficiently.  

3. **File Management**  
   - Creating and deleting files.  
   - Managing directories.  

4. **I/O Management**  
   - Controlling and managing input/output devices.  

---

# Types of Kernel  

## 1. Monolithic Kernel  
- All OS operations are handled inside the kernel.  
- Switching between **user mode** and **kernel mode** occurs via software interrupts.  
- **Fast communication**, but:  
  - Bulky kernel.  
  - Less reliable (a crash in one service may crash the whole system).  

---

## 2. Microkernel  
- Only **essential components** are inside the kernel.  
- Non-essential services (e.g., file management, drivers) run in user space.  
- **Advantages:** Smaller, more reliable, more stable.  
- **Disadvantages:** Slower performance (more user ↔ kernel switching).  
- **Example:** L4, Minix.  

**Communication:**  
- Done via **IPC (Inter-Process Communication):**  
  - **Shared Memory:** One writes, another reads.  
  - **Message Passing:** Separate channel created for message transfer.  

---

## 3. Hybrid Kernel  
- Mix of **monolithic** and **microkernel** features.  
- File management stays in user space, while other functions stay in kernel space.  
- Reduces excessive switching while keeping stability.  
- **Example:** Windows NT, macOS.  

---

## 4. Nano Kernel  
- Extremely small kernel with **minimal hardware abstraction**.  
- Almost all OS services are moved outside the kernel.  
- Used in systems where minimalism and **security** are prioritized.  

---

## 5. Exo Kernel  
- Provides **very low-level hardware access** to applications.  
- Only manages **protection and multiplexing** of hardware resources.  
- Leaves resource management policies to user-level programs.  
- Allows high flexibility but requires complex design.  

---

# System Calls  

System calls act as the **interface** between **user mode** and **kernel mode**.  
- They enable applications to request services from the OS.  
- Almost all system calls are implemented in **C language**.  

---

## Types of System Calls  

1. **Process Control**  
   - Creating and terminating processes.  
   - Loading, executing programs.  
   - Example: `fork()`, `exit()`, `exec()`  

2. **File Management**  
   - Creating, deleting, reading, writing files.  
   - Example: `open()`, `read()`, `write()`, `close()`  

3. **Device Management**  
   - Requesting and releasing devices.  
   - Performing I/O operations on devices.  
   - Example: `ioctl()`, `read()`, `write()`  

4. **Information Management**  
   - Getting and setting system data (date, time, process info).  
   - Example: `getpid()`, `alarm()`, `sleep()`  

5. **Communication Management**  
   - Establishing communication between processes.  
   - Message passing, sockets, and shared memory.  
   - Example: `pipe()`, `shmget()`, `send()`, `recv()`  

---

## ✅ Summary  
- **User Space:** Runs applications without direct hardware access.  
- **Kernel:** Core of OS with process, memory, file, and I/O management.  
- **Kernel Types:** Monolithic (fast but bulky), Microkernel (modular but slower), Hybrid (balanced), Nano (minimalist), Exo (low-level flexibility).  
- **System Calls:** Provide controlled interaction between user programs and the kernel for processes, files, devices, information, and communication.  


# What Happens When We Turn On a Computer?

When a computer powers on, the following sequence takes place:  

---

## 1. Power Distribution  
- Electricity is distributed to all components (CPU, RAM, storage, etc.).  

---

## 2. CPU Loads BIOS/UEFI  
- **BIOS (Basic Input/Output System):** Legacy firmware (older computers).  
- **UEFI (Unified Extensible Firmware Interface):** Modern replacement for BIOS.  

The CPU initializes by loading BIOS/UEFI into memory.  

---

## 3. Hardware Initialization  
- BIOS/UEFI performs **POST (Power-On Self-Test)** to check hardware.  
- Loads settings from memory backed by the **CMOS battery**.  

---

## 4. Boot Device Selection  
- BIOS/UEFI identifies the **boot device** (HDD, SSD, USB, etc.).  
- Passes control to the **boot loader** stored on the boot device.  

- **Old systems:**  
  - **MBR (Master Boot Record):** Stored at disk’s 0th sector, contains boot loader.  

- **Modern systems:**  
  - **EFI Partition:** Contains boot loader files.  

---

## 5. Boot Loader Loads OS  
- Boot loader executes and loads the full operating system.  
- Different OS use different boot loaders:  
  - **Windows:** `bootmgr.exe`  
  - **macOS:** `boot.efi`  
  - **Linux:** GRUB  

✅ All of these steps happen within a few seconds.  

---

# Difference Between 32-bit and 64-bit Operating Systems  

| Feature | **32-bit OS** | **64-bit OS** |
|---------|---------------|---------------|
| **Addressable Memory** | 2³² locations | 2⁶⁴ locations |
| **Instruction Width** | Processes 32-bit per CPU cycle | Processes 64-bit per CPU cycle |
| **Resource Usage** | Limited handling of RAM and CPU | Better utilization of hardware resources |
| **Performance** | Slower, supports ≤ 4 GB RAM | Faster, supports > 4 GB RAM |

---

# Types of Storage in a Computer  

## 1. Primary Memory  
- **Register:**  
  - Smallest storage unit.  
  - Very fast but costly.  
- **Cache Memory:**  
  - Stores frequently used instructions.  
  - Increases execution speed.  
  - Faster but expensive.  
- **Main Memory (RAM):**  
  - Larger capacity.  
  - Slower and cheaper compared to registers and cache.  

---

## 2. Secondary Memory  
- **Electronic Disks (SSD, Flash Storage):** Fast, durable, uses electronics.  
- **Magnetic Disks (HDD, Floppy):** Traditional storage using magnetic fields.  
- **Optical Disks (CD, DVD, Blu-ray):** Uses lasers for reading/writing.  

---

## ✅ Summary  
- On startup, CPU loads **BIOS/UEFI**, performs **POST**, then hands over control to the **boot loader**, which loads the OS.  
- **32-bit vs 64-bit:** 64-bit systems handle more memory, perform faster, and utilize resources better.  
- **Storage:** Registers → Cache → RAM (fastest to slower, most expensive to cheaper), with **secondary storage** for large permanent data.  
