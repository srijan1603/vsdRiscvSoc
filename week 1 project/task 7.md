🧩 P1W1 – Task 7: Running Under an Emulator (QEMU)

🎯 Objective:
Run a bare-metal ELF executable for RV32IMC on QEMU, using UART output mapped to 0x10000000.

✅ Step 1: UART Output Code
~~~bash
#define UART0 ((volatile unsigned char *)0x10000000)

void print_uart(const char *s) {
    while (*s) {
        *UART0 = *s++;
    }
}

int main() {
    print_uart("Hello, RISC-V!\n");
    while (1);
    return 0;
}
This code prints a string to UART.
~~~
UART is memory-mapped at address 0x10000000.

🛠️ Step 2: Compile the ELF Binary
Use the RISC-V GCC toolchain to compile without standard libraries:

~~~bash
riscv32-unknown-elf-gcc \
  -march=rv32imac -mabi=ilp32 -nostdlib \
  -T link.ld start.S hello.c -o hello.elf
-nostdlib: Prevents linking standard libraries.

link.ld: Custom linker script.

start.S: Startup assembly file defining _start.
~~~
🏃 Step 3: Run on QEMU (SiFive E-class)
~~~bash
qemu-system-riscv32 \
  -nographic \
  -machine sifive_e \
  -kernel hello.elf \
  -bios none \
  -serial mon:stdio
-nographic: Disables graphical output.

-bios none: Skips default bootloader.

-serial mon:stdio: Redirects UART to terminal.
~~~
🖥️ Expected Output:
Hello, RISC-V!
The program loops infinitely after printing.

To exit QEMU: press Ctrl + A, then X.
