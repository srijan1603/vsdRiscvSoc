# Step 1: Extract the Toolchain
A. Extract the Toolchain Archive
```bash
cd ~/Downloads
tar -xzf riscv-toolchain-rv32imac-x86_64-ubuntu.tar.gz
```
B. Add the Toolchain to Your PATH
```bash
echo 'export PATH=$HOME/Downloads/riscv/bin:$PATH' >> ~/.bashrc
source ~/.bashrc
```
 C. Confirm Installation
 ```bash
riscv32-unknown-elf-gcc --version
riscv32-unknown-elf-objdump --version
riscv32-unknown-elf-gdb --version
```
![image](https://github.com/user-attachments/assets/cf8aeae8-f9bc-4995-bda7-476f60e14c3a)

![image](https://github.com/user-attachments/assets/6dab2b35-125a-4756-93da-76470fa56f45)
