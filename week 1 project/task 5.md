# Task 5: ABI & Register Cheat-Sheet (RV32)
List all 32 RV32 integer registers with their ABI names and typical calling-convention roles.
## RISC-V Register Cheat Sheet (RV32)

| Register | ABI Name | Role                              |
|----------|----------|-----------------------------------|
| x0       | zero     | Constant 0                        |
| x1       | ra       | Return address                    |
| x2       | sp       | Stack pointer                     |
| x3       | gp       | Global pointer                    |
| x4       | tp       | Thread pointer                    |
| x5–x7    | t0–t2    | Temporaries (caller-saved)        |
| x8–x9    | s0–s1    | Saved registers (callee-saved)    |
| x10–x17 | a0–a7     | Function args & return values     |
| x18–x27 | s2–s11    | Saved registers (callee-saved)    |
| x28–x31 | t3–t6     | Temporaries (caller-saved)        |

Calling Convention Summary

    a0–a7 = Function arguments / Return values

    t0–t6 = Temporaries (caller-saved)

    s0–s11 = Saved registers (callee-saved)

    sp = Stack pointer

    ra = Return address
