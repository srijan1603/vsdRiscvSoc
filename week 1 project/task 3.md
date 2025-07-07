#  Step 3: From C to Assembly
A. Compile to Assembly (.s file)
```bash
riscv32-unknown-elf-gcc -S -O0 -march=rv32imc -mabi=ilp32 hello.c
```
View the Generated Assembly
B.View the Assembly File
```bash
cat hello.s
```bash
    .file   "hello.c"
    .option nopic
    .attribute arch, "rv32imc"
    .text
    .globl  main
    .type   main, @function
main:
    addi    sp,sp,-16          # Function prologue: allocate stack space
    sw      ra,12(sp)          # Save return address
    lui     a0,%hi(.LC0)
    addi    a0,a0,%lo(.LC0)
    call    printf             # Call to printf
    li      a5,0
    mv      a0,a5
    lw      ra,12(sp)          # Function epilogue: restore return address
    addi    sp,sp,16           # Deallocate stack
    ret                        # Return
.LC0:
    .string "Hello, RISC-V!"
```
knowledgw
Prologue:
addi sp,sp,-16: Allocates 16 bytes of stack space.
sw ra,12(sp): Saves the return address to the stack
Epilogue:
lw ra,12(sp): Restores the return address from the stack.
addi sp,sp,16: Frees the allocated stack space.
ret: Returns to the caller.

![image](https://github.com/user-attachments/assets/d8444b49-8400-4c28-939d-070b2745a432)
