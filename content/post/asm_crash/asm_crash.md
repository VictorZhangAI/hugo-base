---
title: "assembly-related"
date: 2025-02-26T20:49:18+08:00
draft: false
tags: ["COA"]
---

# asm & syscalls

move value into register:
```assembly
mov rax, 60
```
dereference a pointer:
```assembly
mov rdi, [1337000]
```

let the asm program executable:
```assembly
.intel_syntax noprefix
.global _start
_start:
<asm_code>
```

exit():
```assembly
mov rdi, <exit_code>
mov rax, 60
syscall
```

write():
```assembly
mov rdi, <1_or_2>
mov rsi, <memory_addr>
mov rdx, <bytes>
mov rax, 1
syscall
```

read():
```assembly
mov rdi, 0
mov rsi, <memory_addr>
mov rdx, <bytes>
mov rax, 0
syscall
```

assemble the program:
```shell
gcc -nostdlib hello.S -o hello # assemble the code
objdump -M intel -d hello # read the code
objcopy --dump-section .text=hello_bin_code hello # extracting binary code
```

arithmetic:
```assembly
add <reg> <opr> # reg += opr
sub <reg> <opr> # reg -= opr
imul <reg> <opr> # reg *= opr
```

specially, for division:
```assembly
div <reg> # rax = {rdx, rax} / reg, rdx = remainder
```
shifting
```assembly
shl <reg1> <reg2> # reg1 << reg2
shr <reg1> <reg2> # reg1 >> reg2
```

and, not, or, xor could be use to process bitwise operations  

stack:
```assembly
push <reg>
pop <reg>
```

jump:
```assembly
jmp reg # jump to the addr in the reg
```

repeat the instruction:
```assembly
.rept 0x51
nop # repeat nop for 0x51 times
.endr
```

compare:

```assembly
cmp dword ptr [edi] 0x12345678
je label
```

ja must jump to a label not an address

