Task 09 – Inline Assembly with GCC
Objective:
Use GCC inline assembly in C to access the RISC-V cycle counter (CSR 0xC00), and understand how operand constraints and inline asm syntax work.

Method:
Below is a simple C function that reads the current cycle count using the csrr instruction. This count tells how many CPU clock cycles have passed since the processor was reset.
~~~bash
#include <stdint.h>

static inline uint32_t read_cycle() {
    uint32_t count;
    asm volatile ("csrr %0, cycle" : "=r"(count));
    return count;
}

int main() {
    uint32_t cycles = read_cycle();
    while (1);
    return 0;
}
~~~
Explanation of Key Parts:
asm volatile: Tells the compiler not to optimize away or move the assembly instruction. This ensures it runs exactly where it's written.

"csrr %0, cycle": RISC-V instruction to read the value of the cycle CSR into %0 (which maps to the output variable).

: "=r"(count): This is the output constraint. = means the variable is write-only, and r means use any general-purpose register.

No input operands or clobbered registers are listed because the instruction only reads from a CSR and writes to one output variable.

Additional Notes:
The cycle CSR (Control and Status Register) holds the number of CPU cycles since the system started.

This kind of inline assembly is commonly used in performance measurement or bare-metal development where low-level access is required.

The use of volatile is critical to prevent the compiler from optimizing out this code during higher optimization levels like -O2.
