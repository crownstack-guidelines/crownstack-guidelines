---
title:  "Build a VM from Scratch"
date:   2017-09-01 11:11:11
author: Gautam Singh
categories:
- blog
tags:
- programming
---

## Build a Virtual Machine From Scratch
> Creating and Optimizing Virtual Machine

Virtual machine is a robust concept to achieve platform independent design for various platforms (operating system: windows, linux, mac). These programming languages are designed above the layer of core architecture (x86, x86_64) and rely on OS system calls. The code is compiled and interpreted to machine languages(binary language). Now, the question arises how this virtual machine attains platform independence for programming languages like Java. Lua and Python etc. Virtual Machines provides an abstraction layer for these programming languages. In any platform, these translators generates an intermediate code which is understandable by virtual machines and  designed for every platform.

### Tools required to build a Virtual Machine
* GCC/Clang, G++, GDB, CMAKE
* Lex, YACC
* Nano, VIM
* Core-libs and Debugging Tool

### Why you should write a Virtual Machine

* You want a deeper understanding of how a computer works. Low-level instructions executed on CPU(addressing modes).
So, to understand virtual machine, a better way is to build it.

* Learn how a programming language works, Its internal architecture. Moreover how to optimize a virtual machine (instruction and memory). JIT(Jist-In-Time compiler) is used in JVM, Python VM, and various other programming languages. And GC(Garbage Collector) to avoid memory leakages and a better way to organize main memory. 

### CPU Architecture

The processor in a computer responsible for executing instruction and performing hardware interactions. The processor has a manual of Mnemonics(assembly language instruction) which wraps binary language instruction. The bandwidth of the processor decides the number of instruction is going to execute in a machine cycle. Which known as the frequency of the processor. The processor also contains General Purpose Register(GPR) like A,B,C,D,E.  These register stores information of various operation going to be performed in a next cycle. They also have special purpose registers like flags, DS, and various other segments to control instructions flow.

### Stack based Virtual Machine

In the stack based virtual machine, which means it's a stack which can perform operations like Push(insertion), Pop(deletion). These are simpler to implement than register based virtual machine.

|  Instruction         | Meaning                                                       |
|----------------------|---------------------------------------------------------------|
|  PUSH 5              | pushes 5 to stack                                             |
|  PUSH 10             | pushes 10 to stack                                            |
|  ADD                 | Pops 2 values from TOS, Adds them and Pushes Back to stack    |                                      
|  POP                 | Pops the Top element in stack and print it                    |
|  SET A 0             | Set A register to 0                                           | 
|  HALT                | Stop the Program                                              |

### Instruction Cycle
Virtual machines are simpler than you might think. They follow a simple pattern, which is **Instruction Cycle** Fetch, Decode and Execute. First, we fetch the next instruction list or code, we then decode that instruction and add to the instruction set and executes that instruction.

###  Makefile
Makefile is used to automate and resolve dependency for our project. C/C++ files need to be compiled each files compilation manually will take a long time and order of their compilation will be a memorize tasks. Makefile does these task with a configuration on various platforms. When Linux introduced software were written in such a way for years.

    SRC_FILES = main.c
    CC_FLAGS = -Wall -Wextra -g -std=c11
    CC = clang

    all:
       ${CC} ${SRC_FILES} ${CC_FLAGS} -o mac

### Program Instruction

We know the assembly instruction needs to be executed then simply put this instruction in enum so that they can be referenced easily.

    typedef enum {
       PSH,
       ADD,
       POP,
       SET,
       HLT
    } InstructionSet;

Now, storing the actual instruction which is to be executed on the processor. Storing these instruction set in Array.

    const int program[] = {
       PSH, 5,
       PSH, 6,
       ADD,
       POP,
       HLT
    };

**Fetching the Current Instruction**
We have stored our instruction in an array. It will be easy to fetch instruction, but virtual machine also holds a variable to know the instruction executing known as a Program Counter(PC), Instruction Pointer(IP).

    #include <stdbool.h>
    #include<stdio.h>
    #include<limits.h>
    #include<math.h> 
    #define sp (registers[SP])
    #define ip (registers[IP])
    bool running = true;
    int IP = 0; 
    int main() {
    typedef enum {
    PSH,
    ADD,
    POP,
    SET,
    HLT
    } InstructionSet;
    const int program[] = {
    PSH, 5,
    PSH, 6,
    ADD,
    POP,
    HLT
    };
    typedef enum {
         A, B, C, D, E, F,
         NUM_OF_REGISTERS
    } Registers; 
    int registers[NUM_OF_REGISTERS];
      while (running) {
        eval(fetch()); // PSH
        if (x == HLT) running = false;
        IP++; // increment instruction pointer
    }
    // This will return the current instruction
    int fetch() {
       return program[ip];
    }
    // Eval Function for HALT 
    void eval(int instr) {
    switch (instr) {
    case HLT:
        running = false;
        break;
    }  
    case PSH: {
            sp++;
            stack[sp] = program[++ip];
            break;
    }
    case POP: {
    // store the value at the stack in val_popped THEN decrement the stack ptr
    int val_popped = stack[sp--];

    // print it out!
    printf("popped %d\n", val_popped);
    break;
    }
    case ADD: {
    // first we pop the stack and store it as 'a'
    int a = stack[sp--];

    // then we pop the top of the stack and store it as 'b'
    int b = stack[sp--];

    // we then add the result and push it to the stack
    int result = b + a;
    sp++; // increment stack pointer **before**
    stack[sp] = result; // set the value to the top of the stack

    // all done!
    break;
    } 
}

**Execute**
Now save the above code snippet as main.c and run the make file using then command in the project directory
    make
