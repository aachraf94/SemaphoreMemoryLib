# Semaphore and Shared Memory Project

This project provides an implementation of semaphore and shared memory operations in C using System V IPC mechanisms. It includes utility functions for creating, initializing, attaching, detaching, and destroying semaphores and shared memory segments. The code is structured to facilitate inter-process communication (IPC).

## Table of Contents
- [Introduction](#introduction)
- [Features](#features)
- [Directory Structure](#directory-structure)
- [Dependencies](#dependencies)
- [Compilation](#compilation)
- [Usage](#usage)
  - [Semaphore Functions](#semaphore-functions)
  - [Shared Memory Functions](#shared-memory-functions)
- [Example](#example)
- [License](#license)

## Introduction
This project demonstrates the usage of System V semaphores and shared memory for implementing basic IPC functionalities. It is ideal for learning and experimenting with low-level synchronization and memory sharing between processes.

## Features
- Create and initialize semaphores
- Perform P (wait) and V (signal) operations on semaphores
- Delete semaphores
- Create, attach, and destroy shared memory segments
- Utility functions for printing semaphore and shared memory details
- Template `main.c` file to guide implementation of a complete IPC workflow

## Directory Structure
```
project/
├── semaphore.c         # Implementation of semaphore-related functions
├── semaphore.h         # Header file for semaphore
├── shared_memory.c     # Implementation of shared memory-related functions
├── shared_memory.h     # Header file for shared memory
├── main.c              # Template for implementing a full IPC workflow
├── Makefile            # Build instructions (optional)
└── README.md           # Project documentation
```

## Dependencies
- GCC compiler
- System V IPC headers (e.g., `<sys/types.h>`, `<sys/ipc.h>`, `<sys/sem.h>`, `<sys/shm.h>`)

## Compilation
To compile the project, use the following command:
```bash
gcc -o ipc semaphore.c shared_memory.c main.c -std=c99
```
This will generate an executable named `ipc`.

## Usage

### Semaphore Functions
- **`get_semaphore`**: Create or retrieve a semaphore using a file path and project ID.
- **`init_semaphore`**: Initialize the semaphore with a specified value.
- **`p`**: Perform the wait (decrement) operation.
- **`v`**: Perform the signal (increment) operation.
- **`delete_semaphore`**: Remove a semaphore.
- **`sem_printer`**: Print details of a semaphore.

### Shared Memory Functions
- **`get_shared_memory`**: Create or retrieve a shared memory segment.
- **`attach_shared_memory`**: Attach the shared memory segment to the process's address space.
- **`detach_shared_memory`**: Detach the shared memory segment from the process's address space.
- **`destroy_shared_memory`**: Remove a shared memory segment.
- **`shm_printer`**: Print details of a shared memory segment.

### Main Program Template (`main.c`)
The `main.c` file provides a template for implementing a complete workflow combining semaphores and shared memory. The sections include:
- Creation of semaphores and shared memory
- Initialization of resources
- Inter-process synchronization and memory sharing logic
- Cleanup and resource deallocation

The template allows users to implement custom logic for IPC use cases.

## Example
### Semaphore Example
```c
semaphore sem;
get_semaphore(&sem, "file_path", 'A');
init_semaphore(sem, 1);
p(sem); // Wait operation
v(sem); // Signal operation
delete_semaphore(sem);
```

### Shared Memory Example
```c
sharedmem shm;
void *shm_addr;
get_shared_memory(&shm, "file_path", 'B', 1024);
attach_shared_memory(&shm_addr, shm);
// Use shared memory (e.g., read/write)
detach_shared_memory(shm_addr);
destroy_shared_memory(shm);
```

## License
This project is open-source and available under the MIT License. Feel free to use, modify, and distribute it as needed.

