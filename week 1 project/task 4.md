# Task 4: Hex Dump & Disassembly
 Step 1: Disassemble the ELF

This shows human-readable assembly from your compiled .elf file:
```bash 
riscv32-unknown-elf-objdump -d hello.elf > hello.dump
```
Then view it:
```bash 
cat hello.dump
```
 
output
```bash
00000000 <main>:
   0: 1141                 addi    sp,sp,-16
   2: c606                 sw      ra,12(sp)
   4: 4501                 li      a0,0
   6: 40b2                 lw      ra,12(sp)
   8: 0141                 addi    sp,sp,16
   a: 8082                 ret
```
Each line contains:

    Address (0:)

    Opcode in hex (1141)

    Mnemonic (addi)

    Operands (sp, sp, -16)

🔹 Step 2: Convert ELF to Intel HEX format

This creates a raw hex dump that you could use for emulators, programmers, etc.:
```bash
riscv32-unknown-elf-objcopy -O ihex hello.elf hello.hex
```
Then:
```bash
cat hello.hex
```
output
```bash
:100000001141C606450140B20141808200000000E7...
```
![image](https://github.com/user-attachments/assets/c3f50360-0674-4bf0-8df9-3fd3336e4a2f)

![image](https://github.com/user-attachments/assets/bd8e77a3-3fb8-4d2a-9d90-741aeb753180)
