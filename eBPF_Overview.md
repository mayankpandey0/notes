# eBPF (Extended Berkeley Packet Filter)

## Overview
eBPF is a revolutionary technology with origins in the Linux kernel that can run sandboxed programs in a privileged context such as the operating system kernel. It is used to safely and efficiently extend the capabilities of the kernel without requiring to change kernel source code or load kernel modules.

## Use Cases
1. **Networking**: eBPF can intercept and manipulate network packets at the lowest levels, allowing for high-performance load balancing and DDoS mitigation.
2. **Observability**: It allows for deep tracing and profiling of both kernel and user-space applications with near-zero overhead.
3. **Security**: eBPF can monitor system calls and block malicious activity in real-time.

## How it works
1. **Write**: eBPF programs are usually written in a restricted subset of C.
2. **Compile**: Compiled into eBPF bytecode using LLVM/Clang.
3. **Verify**: Before execution, the kernel verifies the bytecode to ensure it won't crash the system or loop indefinitely.
4. **JIT**: The bytecode is Just-In-Time compiled to native machine code for maximum performance.
5. **Attach**: The program is attached to kernel hooks (e.g., system calls, network events).

## Tooling
- **Cilium**: A popular CNI (Container Network Interface) for Kubernetes that uses eBPF for networking, security, and observability.
- **BCC (BPF Compiler Collection)**: A toolkit for creating efficient kernel tracing and manipulation programs.
- **bpftrace**: A high-level tracing language for Linux eBPF.
