# 6. Stepping with GDB
Step 1: Launch GDB on your ELF file
```bash 
riscv32-unknown-elf-gdb hello.elf
```
Step 2: Use the simulator
```baash
target sim
```
Step 3: Set a breakpoint at main
```bash
break main
```
Step 4: Run the program
```bash
run
```
output:
```bash
Breakpoint 1, 0x00000000 in main ()
```
Step 5: See all register values
```bash
info registers
```
Step 6: Step one instruction at a time
```bash
stepi
```
Run this command multiple times to walk through the machine instructions.
Step 7: Watch a specific register (e.g., a0)
```bash 
info registers a0
```
 Step 8: Continue Execution
Run until the program finishes:
```bash
(gdb) continue
```
Output:
```bash
Hello, RISC-V!
```
Step 9: Quit GDB
```bash
(gdb) quit
```
