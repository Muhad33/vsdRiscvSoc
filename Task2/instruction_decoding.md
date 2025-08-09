# 🧮 Instruction Decoding – Task 2

---

## **factorial.c**

### **Objective**
Decode 6 RISC-V integer instructions from the disassembled `main` section of `factorial.c` and explain their function.

### **Decoded Instructions**

| Instruction          | Type   | rd   | rs1  | rs2  | funct3 | funct7   | Opcode  | Binary (Approx.)                     | Description                           |
|----------------------|--------|------|------|------|--------|----------|---------|---------------------------------------|---------------------------------------|
| `addi sp,sp,-32`     | I-type | sp   | sp   | —    | 000    | —        | 0010011 | 111111111000 00010 000 00010 0010011  | Decrease stack pointer by 32 bytes   |
| `sd ra,24(sp)`       | S-type | —    | sp   | ra   | 011    | —        | 0100011 | 0000000 00001 00010 011 11000 0100011 | Store return address at 24(sp)       |
| `addi s0,sp,32`      | I-type | s0   | sp   | —    | 000    | —        | 0010011 | 000000001000 00010 000 01000 0010011  | Set s0 to sp + 32                    |
| `li a5,12`           | I-type | a5   | x0   | —    | —      | —        | —       | —                                     | Load immediate value 12 into a5      |
| `sw a5,-20(s0)`      | S-type | —    | s0   | a5   | 010    | —        | 0100011 | 1111111 00101 01000 010 10100 0100011 | Store a5 at -20(s0)                  |
| `jal ra,fact`        | J-type | ra   | —    | —    | —      | —        | 1101111 | —                                     | Jump to `fact()` and save return addr |

**Notes:**
- Decoded from `0x000000000001036e <main>`.
- Covers I-type, S-type, and J-type formats.
- Binary encodings are approximate for clarity.

---

##  **max_array.c**

### **Objective**
Decode 6 RISC-V integer instructions from the disassembled `main` section of `max_array.c`.

### **Decoded Instructions**

| Instruction           | Type   | rd   | rs1  | rs2  | funct3 | funct7   | Opcode  | Binary (Approx.)                     | Description                              |
|-----------------------|--------|------|------|------|--------|----------|---------|---------------------------------------|------------------------------------------|
| `addi sp,sp,-64`      | I-type | sp   | sp   | —    | 000    | —        | 0010011 | 111111110000 00010 000 00010 0010011  | Decrease stack pointer by 64 bytes      |
| `sd ra,56(sp)`        | S-type | —    | sp   | ra   | 011    | —        | 0100011 | 0000000 00001 00010 011 111000 0100011| Store return address at 56(sp)          |
| `sd s0,48(sp)`        | S-type | —    | sp   | s0   | 011    | —        | 0100011 | 0000000 01000 00010 011 110000 0100011| Store s0 at 48(sp)                       |
| `lui a5,0x1d`         | U-type | a5   | —    | —    | —      | —        | 0110111 | 0000000000011101 010 11111 0110111    | Load upper immediate (0x1d << 12) into a5|
| `sw a5,-28(s0)`       | S-type | —    | s0   | a5   | 010    | —        | 0100011 | 1111111 00101 01000 010 100100 0100011| Store a5 at -28(s0)                      |
| `blt a4,a5,<loop>`    | B-type | —    | a4   | a5   | 100    | —        | 1100011 | —                                     | Branch to loop if a4 < a5               |

**Notes:**
- Decoded from `0x0000000000010328 <main>`.
- Shows use of I-type, S-type, U-type, and B-type formats.

## **bitops.c**

### **Objective**  
Decode 6 RISC-V integer instructions from the disassembled `main` section of `bitops.c`.

### **Decoded Instructions**

| Instruction             | Type   | rd   | rs1  | rs2  | funct3 | funct7   | Opcode  | Binary (Approx.)                     | Description                                   |
|-------------------------|--------|------|------|------|--------|----------|---------|---------------------------------------|-----------------------------------------------|
| `addi sp,sp,-32`        | I-type | sp   | sp   | —    | 000    | —        | 0010011 | 111111111000 00010 000 00010 0010011  | Decrease stack pointer by 32 bytes            |
| `sd ra,24(sp)`          | S-type | —    | sp   | ra   | 011    | —        | 0100011 | 0000000 00001 00010 011 11000 0100011 | Store return address into stack frame         |
| `sd s0,16(sp)`          | S-type | —    | sp   | s0   | 011    | —        | 0100011 | 0000000 01000 00010 011 10000 0100011 | Store frame pointer into stack frame          |
| `and a5,a5,a4`          | R-type | a5   | a5   | a4   | 111    | 0000000  | 0110011 | 0000000 00100 01111 111 01111 0110011 | Bitwise AND between `a5` and `a4`             |
| `or a5,a5,a4`           | R-type | a5   | a5   | a4   | 110    | 0000000  | 0110011 | 0000000 00100 01111 110 01111 0110011 | Bitwise OR between `a5` and `a4`              |
| `xor a5,a5,a4`          | R-type | a5   | a5   | a4   | 100    | 0000000  | 0110011 | 0000000 00100 01111 100 01111 0110011 | Bitwise XOR between `a5` and `a4`             |

---

**Notes:**
- Decoded from `0x0000000000010328 <main>`.
- Includes examples of **I-type**, **S-type**, and **R-type** integer instructions.
- Demonstrates **bitwise integer operations** (`and`, `or`, `xor`) along with stack setup instructions.


## **bubble_sort.c**

### **Objective**  
Decode 6 RISC-V integer instructions from the disassembled `main` section of `bubble_sort.c`.

### **Decoded Instructions**

| Instruction           | Type   | rd   | rs1  | rs2  | funct3 | funct7   | Opcode  | Binary (Approx.)                     | Description                                          |
|-----------------------|--------|------|------|------|--------|----------|---------|---------------------------------------|------------------------------------------------------|
| `addi sp,sp,-64`      | I-type | sp   | sp   | —    | 000    | —        | 0010011 | 111111000000 00010 000 00010 0010011  | Decrease stack pointer by 64 bytes                   |
| `sd ra,56(sp)`        | S-type | —    | sp   | ra   | 011    | —        | 0100011 | 0000000 00001 00010 011 111000 0100011| Store return address into stack frame                |
| `sd s0,48(sp)`        | S-type | —    | sp   | s0   | 011    | —        | 0100011 | 0000000 01000 00010 011 110000 0100011| Store frame pointer into stack frame                 |
| `li a5,9`             | I-type | a5   | x0   | —    | 000    | —        | 0010011 | 0000000001001 00000 000 01111 0010011 | Load immediate value 9 into register a5              |
| `sw a5,-24(s0)`       | S-type | —    | s0   | a5   | 010    | —        | 0100011 | 1111111 00101 01000 010 100100 0100011| Store word a5 at offset -24 from frame pointer        |
| `blt a4,a5,<loop>`    | B-type | —    | a4   | a5   | 100    | —        | 1100011 | —                                     | Branch to loop start if a4 < a5                      |

---

**Notes:**
- Decoded from `0x00000000000103fc <main>`.
- Shows use of **I-type**, **S-type**, and **B-type** integer instruction formats.
- Includes stack frame setup, immediate loading, memory store, and branch instructions typical for loop-based algorithms like Bubble Sort.

