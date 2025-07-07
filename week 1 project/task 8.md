📝 Task 8: Exploring GCC Optimisation

🛠️ Step 1: Compile the Same File with Different Optimization Flags
Run the following commands to generate assembly (.s) files:
~~~bash
gcc -O0 -S hello.c -o hello_O0.s
gcc -O2 -S hello.c -o hello_O2.s
~~~
🔍 Step 2: Compare the Assembly Listings Side-by-Side
Use this command to see differences between the files side-by-side:
~~~bash
diff -y hello_O0.s hello_O2.s | less
~~~
🧠 Step 3: Key Differences to Look For and Why They Occur
| 🧠 Optimization Aspect    | 🔧 `-O0` Output                             | 🚀 `-O2` Output                            | 📘 Explanation                                                                 |
|---------------------------|--------------------------------------------|--------------------------------------------|--------------------------------------------------------------------------------|
| Dead Code Elimination     | Keeps all variables and code, even if unused | Removes unused variables and code         | Saves space and CPU time by eliminating redundant instructions                |
| Register Allocation       | Heavy stack usage, frequent memory access   | Uses CPU registers efficiently             | Reduces memory access, speeds up execution                                    |
| Function Inlining         | Functions are called explicitly             | Small functions may be inlined             | Removes function call overhead and enables deeper optimization                |
| Instruction Count         | More straightforward, unoptimized code      | Fewer, optimized instructions              | Smaller and faster code due to optimization                                   |
| Stack Frame Setup         | Full prologue and epilogue always present   | Simplified or omitted if unnecessary       | Avoids overhead from setting up unnecessary stack frames                      |

✅ Conclusion:
This task highlights how compiler optimizations can significantly affect performance, size, and structure of machine code — especially important for embedded and RISC-V development.

