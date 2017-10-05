---
title:  "Parallel Programming"
date:   2017-04-10 11:11:11
author: Gautam Singh
categories:
- blog
tags:
- programming
---

## Parallel Programming Vs Serial Programming

A computer executes their instruction basically with 2 popular models. 
> Serial Computation

> Parallel Computation

### Serial Computation

Traditionally software has been written for serial computation:
* run on a single computer
* instructions are run one after another
* only one instruction executed at a time

![Serial Compuation](https://computing.llnl.gov/tutorials/parallel_comp/images/serialProblem.gif)
Image Credit: Lawrence Livermore

### Von Neumann Architecture
John von Neumann first authored the general requirements for an electronic computer in 1945.
* Data and instructions are stored in memory
* Control unit fetches instructions/data from memory, decodes the instructions and then sequentially coordinates operations to accomplish the programmed task.
* Arithmetic Unit performs basic arithmetic operations
* Input/Output is the interface to the human operator

![Von Neumann Architecture](https://computing.llnl.gov/tutorials/parallel_comp/images/vonNeumann1.gif)
Image Credit: Wikimedia

***

### Parallel Compuation
Simultaneous use of multiple compute sources to solve a single problem.
![Parallel Computation](https://computing.llnl.gov/tutorials/parallel_comp/images/parallelProblem.gif)

**Why use parallel computing?**
* Save time and/or money
* Enables the solution of larger problems
* Provide concurrency
* Use of non-local resources
* Limits to serial computing

**Concepts and Terminology**

|  SISD (Single Instruction, Sigle Data)          | SIMD (Single Instruction, Mulitple Data)        |
|-------------------------------------------------|-------------------------------------------------|
|  **MISD (Multiple Instruction, Single Data)**   | **MIMD (Multiple Instruction, Multiple Data)**  |

### SISD

* Serial computer
* Deterministic execution
* Examples: older generation main frames, work stations, PCs

![SISD](https://computing.llnl.gov/tutorials/parallel_comp/images/sisd.gif)

### SIMD

A type of parallel computer
* All processing units execute the same instruction at any given clock cycle
* Each processing unit can operate on a different data element
* Two varieties: Processor Arrays and Vector Pipelines
* Most modern computers, particularly those with graphics processor units
(GPUs) employ SIMD instructions and execution units. 

![SIMD](https://computing.llnl.gov/tutorials/parallel_comp/images/simd.gif)

### MISD

* single data stream is fed into multiple processing units.
* Each processing unit operates on the data independently via independent instruction streams.
* Few actual examples: Carnegie-Mellon C.mmp computer (1971). 

![MISD](https://computing.llnl.gov/tutorials/parallel_comp/images/misd.gif)

### MIMD

Every processor may be executing a different instruction stream
* Every processor may be working with a different data stream
* Execution can be synchronous or asynchronous, deterministic or nondeterministic
* Examples: most current supercomputers, networked parallel computer clusters and "grids", multi-processor SMP computers, multi-core PCs.
* Note: many MIMD architectures also include SIMD execution sub-components.

![MIMD](https://computing.llnl.gov/tutorials/parallel_comp/images/mimd.gif)

### Parallel Computer Architecture

* Shared memory: all processors can access the same memory
* Uniform memory access (UMA):
     * identical processors
     * equal access and access times to memory

![Parallel Computer Architecture](https://computing.llnl.gov/tutorials/parallel_comp/images/shared_mem.gif)
Image Credit: llnl.gov

### Non-Uniform Memory Access

Not all processors have equal access to all memories
* Memory access across link is slower
* Advantages:
     * user-friendly programming perspective to memory
     * fast and uniform data sharing due to the proximity of memory to CPUs
* Disadvantages:
     * lack of scalability between memory and CPUs.
     * Programmer responsible to ensure "correct" access of global memory Expense.

![Non-Uniform Memory Access](https://computing.llnl.gov/tutorials/parallel_comp/images/numa.gif)
Image Credit: llnl.gov

### Distributed Memory

Distributed memory systems require a communication network to connect inter-processor memory.
* Advantages:
     * Memory is scalable with a number of processors.
     * No memory interference or overhead for trying to keep cache coherency.
     * Cost effective
* Disadvantages:
     * the programmer responsible for data communication between processors.
     * difficult to map existing data structures to this memory organization.

![Distributed Memory ](https://computing.llnl.gov/tutorials/parallel_comp/images/distributed_mem.gif)
Image Credit: llnl.gov

###  Hybrid Distributed Shared Memory

* Generally used for the currently largest and fastest computers
* Has a mixture of previously mentioned advantages and disadvantages.

![Hybrid Distributed Shared Memory](https://computing.llnl.gov/tutorials/parallel_comp/images/hybrid_mem.gif)
Image Credit: llnl.gov
