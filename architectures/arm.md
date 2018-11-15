# ARM architecture

This guide contain basic info about ARM Cortex-A9 processor oriented to embedded system. ARM, originally Acorn RISC Machine, later Advanced RISC Machine, is a family of reduced instruction set computing (RISC) architectures for computer processors, configured for various environments. This section contain basic ARM elements to understand how it works. 

## Concepts

### Typical elements of a computer

* **Processor**: This is the ‘brains' of the system. It is programmed to perform the tasks specific to the application of the embedded system.
* **Memory Controller**: Memory controllers manage the reading and writing of data to and from main memory in an embedded system. Memory controllers reside in on-chip soft cores, providing an interface between the system memory and all other parts of the system.
* **Peripherals**: These are the components around the central processing unit. Peripherals can be implemented as individual integrated circuits, be contained on-chip with the processor, or may reside in an area of programmable logic such as an FPGA.
* **Peripheral Bus**: The second bus creates two separate sections of the system, allowing two arbiters to control and manage communications across the two buses. This allows devices on the peripheral bus to communicate with each other, even when a high-priority processor-memory transaction is taking place on the system bus.
* **System bus**: In an embedded system with multiple buses, the system bus connects the processor, memory controller and other high-speed devices together. As such, it is the bus with the greatest bandwidth in the system.
* **Dynamic RAM (DRAM)**: DRAM is the most common form of memory that is used in computing systems. A DRAM chip consists of a number of memory cells which can each hold 1-bit of data, stored in a capacitor. Every memory cell also features a transistor, which acts as a switch to allow the control circuitry to read or write the state of the capacitor. As both the capacitor and transistor are extremely small, millions of individual memory cells can fit in a single DRAM chip.
* **Static RAM (SRAM)**: SRAM uses a different technology to store information than DRAM. Whereas each bit of memory in DRAM is stored in a capacitor, SRAM uses latches to store the data. Each memory cell requires 4 or 6 latches to store a single bit of data, and therefore requires much more space on a chip than DRAM, making it more expensive.The upside to SRAM is that it does not need to be refreshed, thus making it much faster than DRAM. Due to the expense of SRAM, it is usually only used in high-speed, low-capacity memory chips.
* **Level 1 (L1) Cache**: L1 cache is the smallest form of cache memory, the size of which is typically 8 to 128 KB. It is implemented in the form of SRAM which is built into the fabric of the processor core and, as such, operates at the same clock rate. L1 cache typically consists of two sections: data and instruction caches.
* **Level 2 (L2) Cache**: L2 cache is usually external to individual processing cores, but is located extremely close by. It is larger than L1 cache, typically in the region of 256 to 1024 KB, but has slower access
speeds. L2 cache is in the form of DRAM and is unified in a single section (unlike L1 which
is split into two sections). Larger quantities of data are constantly read in by L2 cache from
main memory before being fed to L1. Level 3 (L3) Cache Level 3 (L3) cache is shared among all processor cores. It is also implemented in DRAM, and is the largest form of cache memory, typically in sizes of 2 MB and upwards.

### Machine code

When writing a software application, it is often in a high-level language (such as C/C++) which is easily understood by the developer, and human-readable. Code in this form is meaningless to a processing system, and must be converted, or compiled, into a form that the processor can understand. The final, low-level, output that is readable by the processor is known as machine code: a stream of binary data relating to the program that the processor is able to interpret and process.

### Opcodes

An opcode is an operation code which uniquely defines a function to be performed a machine code representation of a processor instruction. A processor can execute many different operations, so each instruction is assigned a unique numeric code.

### Instruction sets

The instruction set for a given processor is the basic set of commands which a processor can understand. It contains a specification of each of the opcodes and native commands that can be performed by that processor.

* The instructions are stored in memory in 32 bits word-aligned manner.
* ARM has 3 types of sets:
  * *ARM set*: This is a group of instructions with 32 bits.
  * *Thumb set*: This is a smaller version that uses only 16 bits intructions. C code generated is up to 35% smaller but not fully fledged instruction set.
  * *Thumb-2 set*: This group use 16 or 32 bit. Almost same performance as ARM but up to 25% smaller with full set.
* Common syntax for ARM and Thumb instructions is Unified Assembler Language (UAL)
* Format of a instruction is: INSTRUCTION REGISTER, PARAMS, ..: ```ADD R0, R1, #24```

### Execution cycles

This is the process by which a system retrieves an instruction from memory, determines the required actions for that instruction, and executes those actions. Each instruction execution can be divided into three unique parts.

#### Fetch instruction

The fetch instruction is the first stage of the instruction execution cycle:

1. The program counter register contains a value that corresponds to an address in memory containing the next instruction to be processed.
1. This value is transferred to the memory address register where the control unit checks the value and fetches the corresponding instruction from memory.
1. That instruction is then stored in the memory buffer register before being transferred to the instruction register.
1. The program counter register is advanced by the control unit so that the value matches the memory location of the next instruction to be executed.

#### Decode instruction

The second step is to get the instruction into a form that the processor can understand. Exist 3 types of addressing modes

* Immediate Addressing: This requires no lookup of data as all of the required data is located within the operands of the instruction. This makes immediate addressing the fastest, but least flexible mode.
* Direct Addressing: Operands of instruction contain the memory address of the required data. Required data must be fetched from this address.
* Indirect Addressing: Operands of instruction contain a memory address. Within this memory address is a pointer to the address where the required data is stored. This makes indirect addressing the most flexible, but slowest due to the two data lookups.

#### Execute instruction

Depending on the opcode that was determined by the decode process, a number of different actions can be performed at this stage. In general, there are four main groups of actions:
* Transfer of data between the processor and memory.
* Transfer of data between processor and I/O devices.
* Processing data, such as using the Arithmetic Logic Unit (ALU).
* Control operations that change the sequence of subsequent operations. These can be conditional based on the values in a certain flag register.

### Interrupts

An interrupt is a signal which is generated to indicate to the processor that its attention is required. Interrupts can be generated by hardware processing units and peripherals, and also within the software itself. In hardware, an interrupt signal is an asynchronous signal that is generated by a processing unit to indicate the need for attention from the processor. In software, an interrupt is also an asynchronous event which indicated to the processor that a change in execution is needed. The process of polling the generated interrupts, however, is synchronous.

* Maskable Interrupts (IRQs): The trigger event of a masked interrupt is not always important. It is the task of the programmer to decide whether the event should cause the program to jump to the requested execution or not. Examples of devices which may use maskable interrupts include timers, comparators and ADCs.
* Non-Maskable Interrupts (NMIs): These are interrupts which should never be ignored, and are therefore deemed much more important than maskable interrupts. Events which require NMIs include power-on, external reset (from a physical button) and serious device faults.
* Inter-Processor Interrupts (IPIs): In multiple processor systems, one processor may need to interrupt the operation of another processor. In this situation, an IPI will be generated.

More info in pdfs.

### Buses

A bus provides the interconnection by which processors interface with other processors
and peripherals. Processors, memory controllers and peripherals connect to the bus via a
standard bus interface.

* The address line transfers the memory addresses, or target port identification numbers, to I/O devices.
* The control line governs the control and timing signals of a system, synchronising operations and transmitting control signals such as interrupt requests and acknowledgements.
* The data line is responsible for the transfer of data.

#### Types

* System bus: In an embedded system design, the system bus is the main method of providing communication between the various peripheral and processing cores. In smaller embedded system designs, the system bus may be the only bus that is present within the design. In larger, multiple-bus designs, the system bus will be the bus with the largest bandwidth that connects the memory controller and the processor, as well as any high-speed devices. All remaining peripherals, which do not require such high-speed access to the processor and memory controller, will be connected via the peripheral bus.
* Peripheral bus: In order to split the embedded system design into separate domains, a second bus known as the peripheral bus can be added. This can be for a number of reasons, such as making the distinction between low-speed and high-speed devices or to provide dedicated bandwidth for the communication between a group of peripheral cores. This allows a set of peripherals to communicate between themselves in parallel with any communication on the system bus, such as a processor-memory access.
* Bus bridge: In order to allow the communication between devices on separate buses, such as the processor (on the system bus) requesting data from a peripheral core (on the peripheral bus), a bridge between the two buses is required. A bridge is connected to both buses and communicates requests between them. On one bus the bridge is connected as a bus master, while having a slave connection on the other.

#### Modes

* Master: It has the ability to request access to the bus and, as such, are responsible for initiating data transfers by driving the address and control signals. Bus cycles can be initiated, and other bus modules informed of the bus cycle type.
* Slave: Do not possess the ability to initiate bus cycles, and instead only monitor bus activity. Signals on the address and control lines are decoded, and when addressed, can either place, or accept, data on/from the bus.

## ARM architecture

### Registers

A processor register is a quickly accessible location available to a computer's central processing unit (CPU). In ARM:

![ARM register structure](../images/ARM-register-structure.png)

* Register size: 32 bits long.
* 15 general-purpose registers: R0-R14
* *R13*: Stack Pointer (SP).
* *R14*: Link register (LR).
* *R15*: Program counter (PC).
* *CPSR register*:
  * Condition code:
    * *N* = Negative. Bit 31.
    * *Z* = Zero. Bit 30.
    * *C* = Carry. Bit 29.
    * *V* = Overflow. Bit 28.
  * Interrupt-disable bit:
    * *I* = 1 disables the IRQ interrupts. Bit 7.
    * *F* = 1 disables the FIQ interrupts. Bit 6.
  * Thumb bit:
    * *T* = 0 ARM execution. Bit 5.
    * *T* = 1 Thumb execution. Bit 5.
  * Processor mode: Bit 4-0.

### Memory and I/O

* I/O devices are memory mapped.
* Memory values can be transferred between memory and general-purpose registers using load and store instructions.
* Instructions can R/W words (32 bits), half words (16 bits) or bytes (8 bits)
* There are 2 registers to addressing memory:
  * Base register (mandatory)
  * Magnitude register (optional), 12-bit offset added to instruction or magnitude in the index register.
* Exist 3 access modes:
  * Offset mode, BR + offset.
  * Pre-indexed mode, same way offset mode; subsequently this address replace content of the base register.
  * Post-indexed mode, same way offset mode; subsequently the base register is loaded with a new address determined in the same way as in the offset mode.

![ARM memory addressing modes](../images/ARM-memory-addressing-modes.png)

#### Load instruction

To manage memory, load instruction allow to copy from a memory location into a destination register.

* Format: *LDR Rx, Ry* - Copy into Rx content at the address found in Ry.
* Variations:
  * *LDRB*: Load byte.
  * *LDRSB*: Load signed byte.
  * *LDRH*: Load halfword.
  * *LDRSH*: Load signed halfword.
  * *LDM*: Load multiple

In example:

| Instruction | Mode | Description |
|:---------|:--------|:------------------|
| ```LDR R2, [R6, # − 8]``` | Offset mode | Loads into R2 data from the address in R6 minus 8 |
| ```LDR R2, [R6, #0x200]``` | Offset mode | Loads into R2 data from the address in R6 plus 0x200 |
| ```LDR R2, [R6, − R8]``` | Offset mode | Loads into R2 data from the contents of R8 from the contentes of R6 |
| ```LDR R2, [R6, #0x200]``` | Offset mode | Loads into R2 data from the address in R6 plus 0x200 |
| ```LDR R2, [R6, R8, LSL #4]!``` | Pre-indexed mode | Loads R2 from the location whose address is determined by shifting the contents of R8 to the left by 4 bit-positions (which is equivalent to multiplying by 16) and adding the result to the contents of R6. Subsequently, the generated address is loaded into R6. |
| ```LDR R2, [R6], #20``` | Post-indexed mode | Load into R2 from the address R6. Subsequently, the contents of R6 are modified by adding to them the offset value 20. |

#### Store instruction

* To manage memory, store intruction allow to copy from a general-purpose register into a memory location.
* Format: *STR Rx, Ry* - Copy content of Rx at the address found in Ry.
* Variations:
  * *STRB*: Store byte.
  * *STRH*: Store halfword.
  * *STM*: Store multiple.

#### Load and store format

The format for Load and Store instructions is shown here:

![Format for Load and Store instructions](../images/ARM-format-loadstore.png)

* *Condition*: 31-28 bits.
* *Operation code (OP)*: 27-20 bits.
* *Rn*: Base register. 19-16 bits.
* *Rd*: Destination in Load instructions, Source in Store instruction. 15-12 bits.
* *Offset*: or Rm. 11-0 bits.

### Instructions

* Registers:
  * *LDR Rx,[Ry]* - Load register
  * *STR Rx,[Ry]* - Store register
* Stack:
  * *PUSH* - I.e: *PUSH {R1, R3 − R5}* places the contents of registers R1, R3, R4 and R5 on the stack.
  * *POP* - I.e: *POP {R1, R3 − R5}* restore the content from the stack.
* Used with LDM and STM:
  * *IA* - Increment after. I.e: *LDMIA R3!, {R4, R6 − R8, R10}* with R3 = 1000 will load registers R4, R6, R7, R8 and R10 from address: 1000, 1004, 1008, 1012 and 1016.
  * *IB* - Increment before.
  * *DA* - Decrement after.
  * *DB* - Decrement before.
* Shifter operand:
  * *OP Rd, Rn, Rm*
  * *ASR* - Arithmetic Shift Right
  * *LSL* - Logical Shift Left
  * *LSR* - Logical Shift Right
  * *ROR* - Rotate Right
* Arithmetic
  * *ADD Rd, Rn, shifter_operand* - Add
  * *ADDC* - Add with carry
  * *SUB* - Subtract
  * *SBC* - Subtract with carry
  * *MUL* - Multiply
  * *MLA* - Multiply accumulate
* Logic
  * *AND Rd, Rn, shifter_operand* - And
  * *ORR* - Or
  * *EOR* - Exclusive or
  * *BIC* - bit clear
* Test: There are two instructions that perform logic operations for testing purposes.
  * *TST Rn, shifter_operand* - Test instruction
  * *TEQ Rn, shifter_operand* - Test equivalence
* Move: The Move instructions copy the contents of one register into another, or they place an immediate value into a register.
  * *MOV Rd , shifter_operand* - Normal move into a register
  * *MVN* - Move complement value.
  * *MOVT* - Move 46 high-order bits and leaves low-order unchanged-
  * *MRS* - Copy content of a processor status register to a register.
  * *MSR* - Copy content of a processor status register from a register.
* Comparation: Compare the contents of two registers or the contents of a register and an immediate
value.
  * *CMP* - Compare subtracting the values.
  * *CMN* - Comparte adding the values.
* Branch instruction: The flow of execution of a program can be changed by executing Branch instructions.
  * *B{cond_suffix} LABEL* - LABEL to jump, if condition code flag Z is 1, depending cond_suffix result:
    * *EQ* - Equal zero.
    * *NE* - Not equal.
    * *CS/HS* - Carry set/Unsigned higher or same.
    * *CC/LO* - Carry clear/Unsigned lower
    * *MI* - Minus (negative)
    * *PL* - Plus (positive or zero)
    * *VS* - Overflow
    * *VC* - No overlow
    * *HI* - Unsigned higher
    * *LS* - Unsigned lower or same
    * *GE* - Signed greater than or equal
    * *LT* - Signed less than
    * *GT* - Signed greater than
    * *LE* - Signed less than or equal
    * *AL* - Always
* Subroutine linkage instrucions:
  * *BL destination* - Branch and link
  * *BX Rm* - Branch and exchange

### Assembler directives

This assembler conforms to the widely used GNU Assembler, which is software available in the public domain.

* *.ascii "string"*: A string of ASCII characters is loaded into consecutive byte addresses in the memory.
* *.asciz "string"*: Same as .ascii but each string is followed by a zero byte.
* *.byte expressions*: Expressions separated by commas are specified. Each expression is assembled into the next byte.
* *.data*: Identifies the data that should be placed in the data section of the memory.
* *.end*: Marks the end of the source code file; everything after this directive is ignored by the assembler.
* *.equ symbol, expression*: Sets the value of symbol to expression.
* *.global symbol*: Makes symbol visible outside the assembled object file.
* *.hword expressions*: Expressions separated by commas are specified. Each expression is assembled into a 16-bit number.
* *.include "filename"*: Provides a mechanism for including supporting files in a source program.
* *.org new-lc*: Advances the location counter by new-lc.
* *.skip size*: Emits the number of bytes specified in size; the value of each byte is zero.
* *.text*: Identifies the code that should be placed in the text section of the memory.
* *.word expressions*: Expressions separated by commas are specified. Each expression is assembled into a 32-bit number.

### Operating modes

* *User mode (10000)*: Unprivileged mode which has restricted access to system resources.
* *System mode (11111)*: Provides full access to system resources. It can be entered only from one of the exception
modes listed below.
* *Supervisor mode (10011)*: It is entered when a software interrupt is raised by a program executing a Supervisor Call instruction, SVC. It is also entered on reset or powerup.
* *Abort mode (10111)*: It is entered if a program attempts to access a non-existing memory location.
* *Undefined mode (11011)v: It is entered if the processor attempts to execute an unimplemented instruction.
* *IRQ mode (10010)*: It is entered in response to a normal interrupt request from an external device.
* *FIQ mode (10001)*: It is entered in response to a fast interrupt request from an external device. It is used to provide faster service for more urgent requests.

### Banked registers

To make the processing of exceptions more efficient, some other registers are involved. They are called the banked registers. There is a different set of banked registers for each exception
mode. All exception modes use their own versions of the Stack Pointer, SP_mode, the Link register, LR_mode, and
the Status register, SPSR_mode. The FIQ mode also has its own registers R8 to R12, which are called R8_fiq to
R12_fiq.

![Banked registers for various operating modes](../images/ARM-banked-registers-op.png)

# Technologies

* **MPCore**: The ARM Cortex-A9 MPCore is a 32-bit processor core licensed by ARM.
* **Neon**: It is a technology with 128-bit SIMD (Single Instruction, Multiple Data) architecture extension for the ARM cortex A series.

# Acronyms

* **ABI**: Application Binary Interface.
* **CAN**: Controller Area Network bus.
* **CISC**: Complex Instruction Set Computer.
* **GPIO**: General-purpose input/output.
* **RISC**: Reduced Instruction Set Computer.
* **SIMD**: Single Instruction Multiple Data. Allow multiple operations on a pair of vectors.

# Bibliography

* [ARM](https://en.wikipedia.org/wiki/ARM_architecture) at Wikipedia.
