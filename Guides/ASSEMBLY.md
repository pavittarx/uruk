# Assembly Language Basics
Notes from MCS-012

# Prerequisites 
* Knowledge of Binary, Decimal & Hexadecimal number system.
* Knowledge of Computer Memory and related information.
* General Low Level Computer Knowledge.

[=] Assembly Language is not case-sensitive.


# Registers 

## IA 32 Architecture 
* Ten 32-bit registers.
* Six 16-bit registers.

## Register Categories 
* General Registers
* Control Registers
* Segment Registers

## Group A: General Registers
* Data Registers
* Pointer Registers
* Index Registers

### Data Registers
They are used used for arithmetic, logic & other operations. These are four 32-bit registers (AX, BX, CX & DX).

These are used in three ways -

EAX, EBX, ECX, EDX - 32-bit data registers. 
AX, BX, CX, DX - 16-bit data registers & Lower Halves of 32-bit data registers. <br/>
AH, BH, CH, DH - 8-bit data registers, Upper halves of 16-bit data registers. <br/>
AL, BL, CL, DL - 8-bit Data Registers, Lower Halves of 16-bit data registers.

**AX (Accumulator Register)**  <br/>
This Register is used to store immediate arithmetic & logic results <br/>
The 8051 has a primary & secondary accumulator, the second one is used by instructions when multiplying or dividing. The format splits the 16-bit result between two 8-bit accumulator register A, and the remainder in secondary accumulator B.<br/>
The modern ubiquitous Intel x86 (8080 & 8086), still use primary accumulator EAX, and secondary as EDX. It is used for I/O and most arithmetic instructions.

**BX (Base Register)** <br/>It is used in Index addressing.

**CX (Count Register)** <br/>It stores loop count of iterative statements.

**DX (Data Register)** <br/>It is used in I/O Operations. <br/>It is also used along with AX for multiplication & division operations involving large values. 

### Pointer Register

**IP (Instruction Pointer)** [16 bits] <br/>It stores offset address of instruction to be executed.

[=] IP in association with CS Registeras CS:IP gives complete address of current address in code segment.

**SP (Stack Pointer)** [16 bits] <br/>It provides offset value within the program stack.

[=] SS:SP refers to current position of data/address within the program stack.

**BP (Base Pointer)** [16-bits]<br/>It mainly helps in referencing the parameter variables passed to a subroutine.

[=] SS:BP gives location of the parameter.<br/>[=] DI:BP, SI:BP for special addressing.

### Index Registers

**SI & DI** are used for index addressing, and sometimes for addition & subtraction as well.

**SI (Source Index)** <br/>It is used as a source index for string operations.

**DI (Destination Index)**  <br/>It is used as a destination index for string operations.


## Group B: Control Registers 
These are 32-bit IP registers combined with 32-bit Flag registers. <br/>

**OF (Overflow Flag)** <br/>It indicates overflow of a high order bit (left bit) of data after signed arithmetic operation.

**DF (Direction Flag)** <br/>It determines direction (left/right) for moving or comparing string data. <br/>DF=0, Left to Right Direction <br/>DF=1, Right to Left Direction.

**IF (Interrupt Flag)**  <br/>It determines whether the external interrupts like keyboard input, etc. are ignored/processed. <br/>IF=0, External Interrupts are disabled. <br/>IF=1, External Interrupts are enabled.

**TF (Trap Flag)** <br/>It allows setting the operation of the processor in a single step mode.<br/>The `DEBUG` program, used sets the TF, so we could step through execution of instruction one at a time.

**SF (Sign Flag)** <br/>It shows sign of the result of an arithmetic operation. The sign is set according to the sign of data item following the arithmetic operation. <br/>The sign is indicated by the high order of leftmost bit.<br/>SF=0, Positive Result
SF=1, Negative Result

**ZF (Zero Flag)** <br/>It indicates result of arithmetic/comparison operation. <br/>A non-zero result clears ZF flag to 0. <br/>ZF=1, indicates a Zero Result.

**AF (Auxiliary Carry Flag)**<br/>todo: Update the Auxiliary Carry Flag definition<br/>

It contains carry from bit 3 to bit 4 following an arithmetic operation.
It is used for specialized arithmetic.
The AF is set to 0, when 1 byte arithmetic operation causes a carry from bit 3 to bit 4.

**PF (Parity Flag)** <br/>
It indicates total number of 1 bits in the result obtained from an arithmetic operation. <br/>PF=0, Even number of 1 bits.
PF=1, Odd number of 1 bits.

**CF (Carry Flag)** <br/>It contains the carry of 0/1 from  high order (leftmost) bit after an arithmetic operation.<br/>It stores content of last bit of shift/rotate operation.

The table indicates the position of flag bits in the 16-bit flag register.

<table>
<td>Bit No </td>
<td> 15 </td>
<td> 14 </td>
<td> 13 </td>
<td> 12 </td>
<td> 11 </td>
<td> 10 </td>
<td>  9 </td>
<td>  8 </td>
<td>  7 </td>
<td>  6 </td>
<td>  5 </td>
<td>  4 </td>
<td>  3 </td>
<td>  2 </td>
<td>  1 </td>
<td>  0 </td>
</tr>
<tr>
<td> Flag </td>
<td> - </td>
<td> -</td>
<td> -</td>
<td> -</td>
<td> O</td>
<td> D</td>
<td> I</td>
<td> T</td>
<td> S</td>
<td> Z</td>
<td> -</td>
<td> A</td>
<td> -</td>
<td> D</td>
<td> -</td>
<td> C</td>
</tr>
</table>

## Group C: Segment Registers

* Code Segment
* Data Segment 
* Stack Segment

### Code Segment
It contains all instructions to be executed. <br/>A 16-bit code segment (CS) register stores the starting address of the code  segment.

### Data Segment 
It contains data, constants & work areas. <br/>A 16-bit data segment (DS) register stores the starting address of data segment.

### Stack Segment
It contains data & return addresses of procedures/subroutines. It is implemented as a `Stack` data structure.<br/>The Stack Segment (SS) register stores the starting address of the stack. The segment registers stores the starting address of a segment. In order to get the exact location of data/instruction, an offset/displacement value is required. <br/>To reference any memory location in a segment, the procedure combines the segment address in the segment register with the offset value of the location.

[=] There are few other segment registers apart from CS, DS & SS. `ES (Extra Segment), FS, GS` which provide additional segments for storing data.


### More about Segments 
A segment starts with an addresss evenly divisible by 16 (or hexadecimal 10, 0x10). <br/>The rightmost hex digit in all such memory addresses is 0, which is not generally stored in segment register 


# System Calls
System calls are API's for interface between the user space & kernel space.

## Linux System Calls 
1. Put the System Call Number in EAX register.
2. Store arguments to the system call in the registers EBX, ECX, etc.
3. Call the relevant interrupt.
4. The result is usually returned in EAX register. 

There are six registers, `EBX, ECX, EDX, ESI, EDI, EBP` that stores arguments of the system call used.\
These registers take consecutive arguments starting with the EBX register. If there are more than 6 arguments the memory location of the first register is stored in EBX register.

### Use of System Call sys-exit

``` 
mov eax, 1 ; System Call number (sys-exit)
int 0x80   ; call Kernel
```

## Common System Calls (Linux)
|Name|%eax|%ebx|%ecx|%edx|%esx|%edi|
|---|---|---|---|---|---|---|
|sys_exit|1|int|-|-|-|-|
|sys_fork|2|struct pt_regs|-|-|-|-|
|sys_read|3|unsigned int|char*|size_t|-|-|
|sys_write|4|unsigned int|const char*|size_t|-|-|
|sys_open|5|const char*|int|int|-|-|
|sys_close|6|unsigned int|-|-|-|-|

# Addressing Modes
In assembly language, most of the instructions require operands to be processed. An operand address provides the location where the data to be processed is stored.

When an instruction requires two operands,<br/>The first operand is generally the destination, that containes data in register/memory location. <br/>The second operand is the source, it contains either data to be delivered or the address of register/memory loaction, that contains data.

The very basic modes of addressing are - 
* Register Addressing
* Immediate Addressing
* Memory Addressing

### Register Addressing 
A register contains the operand. It can be first, second or both operands, depending upon the instruction.

``` 
mov dx, tax_rate ; register contains first operand
mov count, cx    ; register contains second operand
mov eax, ebx     ; both first & second operands are in a register
```
### Immediate Addressing 
The operand has an constant/direct value, or an expression sometimes.\
When an expression uses immediate addressing, the first operand can be  register/memory location but, the second operand is an immediate constant.\
The first operand defines length of data.

```
byte_value db 150  ; a byte value is defined
word_value dw 300  ; a word value is defined
add byte_value, 65 ; an immediate aoperand 65 is added
mov ax, 45h        ; immediate constant 45h is transferred to AX
```

### Direct Addressing 
When operand are specifie in memory addresing mode, direct access to the main memory is required (usually to data segment). This mode results in slower processing of data.\
In order to locate exact location of data in memory, we need starting address of the segment (typically found in `DS` register), and an offset value, which is also called `Effective Address`.

In direct addressing mode, the offset value is specified directly usually indicated by a variable name. The assembler calculates the offset value & maintains a symbol table, which stores the offset values of all variabled used in the program. 

In direct memory addressing, one of the operands refers to a memory location & the other operand references a register. 

```
add byte_value, dl ;adds the register in the memory location
mov bx, word_value ;operand is transferred to register from memory.
```

### Direct Offset Addressing 
This addressing mode uses the arithmetic operators to modify an address.

Following definitions, defines tables of data -->

```
byte_table db 14,15,22,45     ; table of bytes
word_table dw 134,345,564,270 ; table of words 
```

The following operation access data from tables in the memory inro registers.

```
mov cl, byte_table[2] ; gets 3rd element of byte_table
mov cl, byte_table+2  ; gives 3rd elemnt of byte_table

mov cx, word_table[3] ; gets 4th element of word_table
mov cx, word_table+3  ; gets 4th element of word_table
```

### Indirect Memory Addressing
This mode utilizes the computers ability of segment offset addressing.\
The base registers `EBX`/`BX`, `EBP`/`BP` & the index registers `DI,SI` coded with square brackets for memory refernces are used for this purpose.

Indirect addressing is generally used for variables containing several elements like arrays. The starting address of array is stored in (say) EBX register.


### Accessing Different elements of a variable 

```
my_table times 10 dw 0 ; allocates 10 words (2 bytes) each initialized to 0

mov ebx, [my_table]    ; effective address of my_table in ebx
mov [ebx], 110         ; my_table[0]=110
add ebx,2              ; ebx=ebx+2
mov [ebx], 123         ; my_table[1]=123

```

## Variables: Assembly Language 

Assemblers are computer programs which translates assembly language to an object file or machine language format. The popular ones are 
`MASM`, `NASM`, `TASM`, `WASM`.

NASM provides various `define` directives to reserve storage space for variables. The define assembler directive is used for allocation of storage space. It can be used to reserve & initialize one or more memory bytes.

### Allocating Storage Space for data

(variable-name) (directive) [,initial-value]

The assemble associates an offset value for each variable name  defined in the data segment.


| Directive | Purpose | Storage Space |
|---|---|---|
|DB | Define Byte | allocates 1 byte|
|DW| Define Word| allocates 2 bytes|
|DD|Define Double Word|allocates 8 bytes|
|DT|Define Ten Bytes|allocates 10 bytes|

Example -->
``` 
choice db 'y'
numbr dw 123456
neg_num dw -123456
real_num dd 1.235
real_num2 dq 125.27
```

#### Rules 
1. Each byte of a character is stored in its ASCII value in hexadecimal 
2. Each decimal value is automatically converted to its 16-bit binary equivalent & stores=d as a hexadecimal number.
3. Processor uses the little-endian byte ordering.
4. Negative numbers are converted into 2's complement presentation.
5. Short & Long floating point numbers are represented using 32-bits & 64-bits respectively.

### Allocating Space for Unintialized Data 
The reserve directives are used for reserving space for uninitialized data. The reserve directive takes single operand that specifies the number of unit space to be reserved.

Five basic forms of reserve directive -

| Directive | Purpose |
| --- | --- |
| RESB | Reserves a Byte|
| RESW | Reserves a Word|
| RESD | Reserves a Double Word|
| RESQ | Reserves a Quad Word|
| REST | Reserves Ten Bytes|

### Multiple Definitions
You can have multiple definitions in a program. 

```
choice db 'y'  ; ASCII of y is 79h
num1 dw 1237   ; 1237D is 4d5h
num2 dd 123456789   ; 123456789d = 75bcd15h
```
[=] The assembler allocates continous memory locations for multiple variable definitions.

### Multiple Initializations
The times directive allows multiple intializations with the same value.

```
marks times 9 dw 0 ; an array of marks sized 9, with each value set to 0
```

## Constants: Assembly Language

There are several directives provided by NASM.
* EQU
* %assign
* %define

### The EQU directive
It is used for defining constants.

> constant_name equ expression

```
total_students equ 50ca
```

### The %assign directive
It can be used to define numeric constants like the `equ` directive. <br/>
This directive also allows redefinitions/

```
%assign total 10 ; initial definition
%assign total 27 ; redefinition
 
```

### The %define directive
The %define directive allow defining both numeric and string constants. It is similar to #define in C.
```
%define ptr [ebp+4]
```

It allows redifination and is also case-sensitive.

## Arithmetic Instructions: Assembly Language

### The INC instruction

The inc instruction is used to increment an operand by 1. It works on a single operant that can either be in a register or memory.

> inc destination

The operand destination can be 8/16/32-bits.

```
inc cx      ; increments 32-bit register
inc [count] ; increments count variable
```

### The DEC instruction
It is used to decrement an operand by 1.
 > dec destination

 The operand destination can be 8/16/32-bits.

```
dec cx      ; decrements 32-bit register
dec [count] ; decrements count variable
```
### The ADD and SUB instructions

These are used for performing simple addition/subtraction of binary data i.em for adding or subtraction operand data.

> add/sub destination, source

The ADD/SUB instruction can take place between 
* Register to Memory and vice-versa
* Register to Register
* Register to Constant Data
* Memory to Constant Data

[=] Memory to memory operations are not possible as an ADD/SUB operation sets(clears) the overflow & carry flags.

### The MUL/IMUL Instruction
These two instructions are used for multiplying data. <br/>
The MUL handles unsigned data. IMUL(Integer Multiply) handles signed data. <br/>
Both of these operations affect the carry and overflow flags.

> MUL/IMUL multiplier

Multiplicand in both the cases will be in an accumlator register. The result of multiplication is stored in two registers depending upon the size of multiplicant & multiplier,

<b> Case 1: Two Bytes are multiplied </b><br/>
* Multiplicand in the AL register.
* The multiplier is a byte in memory (or stored in another register).
* The product gets stored in AX: High order 8-bits are stored in AH, while low order 8-bits in the AL register. 

```
[AL] x [8-bit source] = [AH][AL]
```

<b> Case 2: Two One Word values are multiplied. </b><br/>
* Multiplicand is stored in AX register.
* Multpiler is a word stored in memory or in another register. say, DX register.
* The resultant double word needs two registers. The high order bits (leftmost portion) gets stored in DX and the low order bits (rightmost portion) gets stored in AX.

```
[AX] x [16-bit source] = [DX][AX]
```

<b> Case 3: Two Double Word values are multiplied. </b><br/>
* Multiplicand stored in EAX
* Multiplier in memory or another register.
* Product is stored in EDX:EAX registers. EDX contain high order bits, while EAX contains low order bits.

```
[EAX][32-bit source] = [EDX][EAX]
```

### The DIV/IDIV Instructions 
The division operation generated two elements: a quotient & a remainder. <br/>
In case of multiplication, overflow does not occur because double length registers are used, to store the product. However, in division operation overflow may occur. <br/>

The DIV operation is used for unsigned data, while IDIV(Integer Division) is used for signed data.

> DIV/IDIV divisor

It must be noted
* Dividend is stored in accumlator.
* Both the instructions can work with 8/16/32-bit operands.
* The operation affects all six status flags.

<b> Case 1: When divisor is 1 byte long </b><br/>
* Dividend(assumed) : AX [16-bits]
* Quotient : AL Register
* Remainder: AH Register

```
[16-bit divident] / [AX] = [AL][AH]
```


<b> Case 2: When Divisor is One Word long </b><br/>
* Dividend: DX:AX
* Quotient: AX
* Remainder: DX

```
[32-bit dividend] / [DX:AX] = [AX][DX]
```

<b>  Case 3: When divisor is Doube Word</b><br/>
|Fields |  Registers|
|---|:---:|
| Dividend | EDX:EAX|
| Remainder|  EDX |
| Quotient | EAX |

```
[EDX:EAX] / [32-bit divisor] = [EDX] [EAX]
```

## Logical Instructions : Assembly Language
The processor instruction set provides instructions such as AND, OR, XOR, TEST & NOT boolean logic which tests, sets and clears the bits acquired to the need of program.

|Instruction| Format|
|---|---|
| AND | AND operand1, operand 2|
| OR | OR operand1, operand 2|
| XOR | XOR operand1, operand 2|
| TEST | TEST operand1, operand 2|
| NOT | NOT operand|

The first operand in all the cases should either be stored in a register or memory.

### AND Instruction
It is used to support logical operations by performing bitwise AND operation. <br/>
It returns 1 if the matching bits from both the operands are 1, otherwise 0.

Let operand1 is 0101, and operand2 is 0011. The AND operation among them results in 0001 , which is stored in operand 1.

<b> Check whether an operand is odd or even? </b><br/>
This can be simply done by chacking the least significant bit of the number. If the bit is 1, the number is odd otherwise even.

Example: 
```
AND AL, 01H
AND AL, 00H
```

### OR Instruction
It is used for supporting logical expression by performing bitwise OR operation..
It returns 1, if matching bits from either or both are 1. It resturns 0, if both the bits are 0.

Let operand1 has 0101, and operand2 has 0011 stored in them. After OR operation on them, the result in operand1 is 0111.

[=] The OR operation can be used for setting one or more bits.

### XOR Instruction
It implements bitwise XOR operation. The XOR operation sets the resultant bit to 1, if and only if the bits from operands are different else it sets them to 0.
 
Let operand1 contains 0101, and operand2 contains 0011. After XOR operation, operand1 has 0110 stored.

[=] XOR'ing an operand with itself sets the operand to 0. This is used to clear the register.

### TEST Instruction
It works same as AND operation but unlike AND it does not change the first operand.

### NOT Operation
The NOT instruction implements the bitwise NOT operation. NOT operation reverses the bit in the operand.

## Conditions: Assembly Language
The conditional execution in assembly is achieved ny several looping and branching instructions. 

### Conditional Instructions
1. Unconditional JUMP <br/>
This is performed using JMP instruction. The conditional execution often involves a transfer of control to the address of an instruction that does not follow the currently executing instruction.
The transfer of control maybe (forward: to execute a new set of instructions) or (backward: to re-execute same steps).

2. Conditional JUMP <br/>
This is performed by a set of Jump instructions. j[condition] depending upon the condition. The conditional instructions transfer the control by breaking the flow and they do it by changing offset value in IP.

Conditional jump on unsigned data used for logical operations.

|Instruction|Descrition|Flags Tested |
|---|---|:---:|
|JE/JZ|Jump Equal/Jump Zero| ZF |
|JNE/JNZ|Jump Not Equal/Jump Not Zero| ZF |
|JA/JNBE|Jump Above/Jump Not Below/Equal| CF,ZF |
|JB/JNAE|Jump Below/Jump Not Above Equal| CF |z
|JBE/JNA|Jump Below Equal / Jump Not Above| AF, CF |
