# 🧮 Instruction Decoding (factorial.c)

Below are 6 RISC-V integer instructions decoded from the disassembled main section of `factorial.c`.

| Instruction       | Opcode  | rd    | rs1   | rs2   | funct3 | funct7   | Binary (Approx.)        | Description                  |
|------------------|---------|-------|-------|-------|--------|----------|--------------------------|------------------------------|
| `1101`           | addi    | sp    | sp    | imm   | 000    | —        | 000000000010 00010 000 00010 0010011 | sp = sp - 32 (alloc stack) |
| `ec06`           | sd      | ra    | sp    | imm   | 011    | —        | 0000000xxxxx xxxxx 011 xxxxx 0100011 | store ra at 24(sp)         |
| `1000`           | addi    | s0    | sp    | imm   | 000    | —        | 000000000100 00010 000 01000 0010011 | s0 = sp + 32               |
| `47b1`           | li      | a5    | x0    | 12    | —      | —        | —                        | load immediate: a5 = 12     |
| `fef42623`       | sw      | a5    | s0    | -20   | 010    | —        | 1111111xxxxx xxxxx 010 xxxxx 0100011 | store a5 at -20(s0)        |
| `f9dff0ef`       | jal     | ra    | PC    | imm   | —      | —        | —                        | call `fact()` function       |

---

### 📌 Notes:

- These are decoded from address `0x000000000001036e <main>` section.
- Instructions include common types: **I-type, S-type, and J-type**.
