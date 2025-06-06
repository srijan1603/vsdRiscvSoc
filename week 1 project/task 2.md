# Step 2: Compile “Hello, RISC-V”
A. Create the C Source File
```bash
cat > hello.c <<EOF
#include <stdio.h>

int main() {
    printf("Hello, RISC-V!\\n");
    return 0;
}
EOF
```
 B. Compile with the RISC-V GCC Toolchain
```bash
riscv32-unknown-elf-gcc -march=rv32imc -mabi=ilp32 -o hello.elf hello.c
```
C. Verify the Output ELF Binary
```bash
file hello.elf
```
output -
```bash
hello.elf: ELF 32-bit LSB executable, UCB RISC-V, ...
