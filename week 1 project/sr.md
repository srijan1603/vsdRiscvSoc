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
