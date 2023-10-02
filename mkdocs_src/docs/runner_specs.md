# Specifications of compute instances in Cloud-V

This document contains the specifications of the compute instances available for users to run builds in Cloud-V. The term "Compute Instance", can also be safely interchanged with the terms "Build Executor" and "Runner".

| Name String | Architecture | Cores | Memory |
| ---- | ------- | -------------- | ------------ |
| x86_runner1 (or) qemuusermode_runner1 | x86_64 | 4 | 8GiB |
| x86_runner2 | x86_64 | 1 | 512MiB |
| dell5559 | x86_64 | 4 | 8GiB |
| rasp4-1 | aarch64 | 4 | 4GiB |
| riscv64_runner1 | riscv64 | 2 | 2GiB |
| sf1-1 | riscv64 | 2 | 8GiB |
| sf1-2 | riscv64 | 2 | 8GiB |
| sf1-3 | riscv64 | 2 | 8GiB |
| sf2-1 | riscv64 | 4 | 8GiB |
| sf2-2 | riscv64 | 4 | 8GiB |
| sf2-3 | riscv64 | 4 | 8GiB |
| sf2-4 | riscv64 | 4 | 8GiB |
| sf2-5 | riscv64 | 4 | 8GiB |
| unleashed1-1 | riscv64 | 4 | 8GiB |
| unleashed1-2 | riscv64 | 4 | 8GiB |

***Note:** The qemuusermode_runner1 and x86_runner1 are one and the same runner. The purpose of creating two separate executors for same hardware is that `x86_runner1` is supposed to be specifically for x86 architecture whereas `qemuusermode_runner1` is specifically for the users who want to cross compile source code for riscv64 architecture and then use qemu-usermode to execute them. Nevertheless, the tooling available for `x86_runner1` can also be used for `qemuusermode_runner1`*
