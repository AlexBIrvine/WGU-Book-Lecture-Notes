---
Date: 2019/05/15
---

## Overview

1. We are in the third tech revolution (Agricultural, Industrial, **Informational**)
2. Different classes of computers exist based on size (PC, server, Embedded, PMD)
3. There are 8 patterns:
   1. Design for Moore's Law
   2. Use Abstraction to Simplify Design
   3. Make the Common Case Fast
   4. Performance via Parallelism
   5. Performance via Pipelining
   6. Performance via Prediction
   7. Hierarchy of Memories
   8. Dependability via Redundancy
4. Your high level code is turned into assembly with a Compiler, then turned into machine code with an assembler.
5. **Systems software**: OS, compiler, loader, assembler.
6. A LCD allows light to be transmitted or blocked in order to show a picture.
7. Pixels are 24 bits, 8 per color.
8. 3 Types of memory to memorize:
   1. DRAM (Dynamic)
   2. Cache
   3. SRAM (Static)
9. Modern chips are built from silicon in 6 steps:
   1. Silicon **ingots** are gathered and sliced to make wafers.
   2. **Wafers** are put through 20~40 processing steps to make **patterned wafers**.
   3. **Patterned wafers** are tested and a map of good/bad parts is created.
   4. **Wafers** are then sliced into **dies**.
   5. Good **dies** are bonded into **packaged dies**.
   6. **Packaged dies** are tested one last time and **ship** if good.
10. Calculating performance takes many steps, (see formula's at end of section.)
11. The System Performance Evalauation Cooperative (**SPEC**) exists and uses 12 benchmarks.
12. Power wall was hit with the Pentium 4 Prescott chips, where it was too hot to run at the given CPU speed.
13. Post Pentium 4, multicore processors were introduced. The need for **parallel programming** was increased.
14. Optimization of hardware/software has a calculation through **Amdahl's law**.

## Formulas

$Time = Seconds/Program = \frac{Instructions}{Program} x \frac{Clock Cycles}{Instructions} x \frac {Seconds}{Clock Cycle}$  
$Energy = Capacitive$ $load$ x $Voltage^2$  
$Power = k$ x $Voltage^2$ x $Frequency$

## Definitions by section:

### 2.1

<u>**Personal computer (PC)**</u>: A computer designed for use by an individual, usually incorporating a graphics display, a keyboard, and a mouse.  
<u>**Server**</u>: A computer used for running larger programs for multiple users, often simultaneously, and typically accessed only via a network.  
<u>**Supercomputer**</u>: A class of computers with the highest performance and cost; they are configured as servers and typically cost tens to hundreds of millions of dollars.  
<u>**Embedded computer**</u>: A computer inside another device used for running one predetermined application or collection of software.  
<u>**Personal mobile devices (PMDs)**</u>: A small wireless device to connect to the Internet; they rely on batteries for power, and software is installed by downloading apps. Conventional examples are smart phones and tablets.  
<u>**Cloud computing**</u>: Refers to large collections of servers that provide services over the Internet; some providers rent dynamically varying numbers of servers as a utility.  
<u>**Software as a Service (SaaS)**</u>: Delivers software and data as a service over the Internet, usually via a thin program such as a browser that runs on local client devices, instead of binary code that must be installed, and runs wholly on that device. Examples include web search and social networking.

### 2.3

<u>**Systems software**:</u> Software that provides services that are commonly useful, including operating systems, compilers, loaders, and assemblers.  
<u>**Operating system**:</u> Supervising program that manages the resources of a computer for the benefit of the programs that run on that computer.  
<u>**Compiler**:</u> A program that translates high-level language statements into assembly language statements.  
<u>**Binary digit (or bit)**:</u> One of the two numbers in base 2 (0 or 1) that are the components of information.  
<u>**Instruction**:</u> A command that computer hardware understands and obeys.  
<u>**Assembler**</u>: A program that translates a symbolic version of instructions into the binary version.  
<u>**Assembly language**</u>: A symbolic representation of machine instructions.  
<u>**Machine language**</u>: A binary representation of machine instructions.  
<u>**High-level programming language**</u>: A portable language such as C, C++, Java, or Visual Basic that is composed of words and algebraic notation that can be translated by a compiler into assembly language.

### 2.4

<u>**Input device**</u>: A mechanism through which the computer is fed information.  
<u>**Output device**</u>: A mechanism that conveys the result of a computation.  
<u>**Memory**</u>: Stores instructions and data.  
<u>**Control**</u>: The component that commands the datapath, memory, and I/O devices according to the instructions of the program.  
<u>**Datapath**</u>: Performs computations.

<u>**Liquid crystal display**</u>: A thin layer of liquid polymers that can be used to transmit or block light according to whether a charge is applied.  
<u>**Active matrix display**</u>: A liquid crystal display using a transistor to control the transmission of light at each individual pixel.  
<u>**Pixel**</u>: The smallest individual picture element. Involves 24 bits, with 8 bits for each of red, blue, and green.  
<u>**Frame Buffer**</u>: Where the represented onscreen is stored and the bit pattern per pixel is read out to the graphics display at the refresh rate.

<u>**Integrated circuit(IC)**</u>: A device combining dozens to millions of transistors.  
<u>**Central processor unit (CPU)**</u>: The active part of the computer, which contains the datapath and control.  
<u>**Instruction set architecture**</u>: An abstract interface between the hardware and the lowest-level software that encompasses all the information necessary to write a machine language program that will run correctly, including instructions, registers, memory access, I/O, and so on.  
<u>**Application binary interface (ABI)**</u>: The user portion of the instruction set plus the operating system interfaces used by application programmers. It defines a standard for binary portability across computers.

<u>**Memory**</u>: The storage area in which programs are kept when they are running and that contains the data needed.  
<u>**Dynamic random access memory (DRAM)**</u>: Memory built as an integrated circuit; it provides random access to any location.  
<u>**Cache memory**</u>: A small, fast memory that acts as a buffer for a slower, larger memory.  
<u>**Static random access memory (SRAM)**</u>: Memory built as an integrated circuit, but faster and less dense than DRAM.  
<u>**Volatile memory**</u>: Storage, such as DRAM, that retains data only if it is receiving power.  
<u>**Nonvolatile memory**</u>: A form of memory that retains data even in the absence of a power source and that is used to store programs between runs.  
<u>**Main/Primary memory**</u>: Memory used to hold programs while they are running.  
<u>**Secondary memory**</u>: Nonvolatile memory used to store programs and data between runs; typically consists of flash memory in PMDs and magnetic disks in servers.  
<u>**Magnetic disk**</u>: Also called hard disk.  
<u>**Flash memory**</u>: A nonvolatile semiconductor memory. It is cheaper and slower than DRAM but more expensive per bit and faster than magnetic disks.

### 2.5

<u>**Transistor**</u>: An on/off switch controlled by an electric signal.  
<u>**Very large-scale integrated (VLSI)**</u>: A device containing hundreds of thousands to millions of transistors.  
<u>**Silicon**</u>: A natural element that is a semiconductor.  
<u>**Semiconductor**</u>: A substance that does not conduct electricity well (only partially lets electrons through).  
<u>**Silicon crystal ingot**</u>: A rod composed of a silicon crystal.  
<u>**Wafer**</u>: A slice from a silicon ingot used to create chips.  
<u>**Die**</u>: The individual rectangular sections that are cut from a wafer.  
<u>**Yield**</u>: The percentage of good dies from the total number of dies on the wafer.

### 2.6

<u>**Response/execution time**</u>: The total time required for the computer to complete a task.  
<u>**Throughput/bandwidth**</u>: The number of tasks completed per unit time.  
<u>**CPU time**</u>: The actual time the CPU spends computing for a specific task.  
<u>**User CPU time**</u>: The CPU time spent in a program itself.  
<u>**System CPU time**</u>: The CPU time spent in the operating system performing tasks on behalf of the program.  
<u>**Clock cycle**</u>: The time for one clock period, usually of the processor clock, which runs at a constant rate.  
<u>**Clock period**</u>: The length of each clock cycle.  
<u>**Clock cycles per instruction (CPI)**</u>: Average number of clock cycles per instruction for a program fragment.  
<u>**Instruction count**</u>: The number of instructions executed by the program.

### 2.9

<u>**Workload**</u>: A set of programs run on a computer that is either the actual collection of applications run by a user or constructed from real programs to approximate such a mix.  
<u>**Benchmark**</u>: A program selected for use in comparing computer performance.  
<u>**SPEC (System Performance Evaluation Cooperative)**</u>: An effort supported by multiple vendors to create a standard set of benchmarks.
