## Call sys_execve with binsh argument

execve() executes the program referred to by pathname.  This causes the program that is currently being run by the calling process to be replaced with a new program, with newly initialized stack, heap, and (initialized and uninitialized) data segments.
In this case we are gonna exploit the program, call sys_execve and use the pathname /bin/sh to spawn a shell. 

### Security

In this case ASLR and NX will be enable. Address space layout randomization (ASLR) is a computer security technique involved in preventing exploitation of memory corruption vulnerabilities. In order to prevent an attacker from reliably jumping to, for example, a particular exploited function in memory, ASLR randomly arranges the address space positions of key data areas of a process, including the base of the executable and the positions of the stack, heap and libraries but doesn't apply in the .text (where the gadgets are located) , .data, .rodata and .bss sections.

![image](https://user-images.githubusercontent.com/87600765/175817705-2ad50828-4ac0-4d8f-91e7-f29c7968f9d1.png)

This technique is really useful when the binary is statically linked s you can't do a ret2plt or something else. 

### Practice

You can found the binary [here](https://github.com/B1rby/Art-of-Exploitation/blob/main/rop/ret2mprotect/vuln.c). To compile it use this command. Of course you need to enable ASLR with the command below

```bash
└─# gcc vuln.c -o vuln -fno-stack-protector -no-pie -static
```

### sys_execve

Of course for this we will follow the syscall table.
![image](https://user-images.githubusercontent.com/87600765/175819535-cb7fd23e-eee9-4e95-b8e6-98a47e13d70c.png)

##### Gadgets

We will use only gadgets for it so according to the syscall table we will need to put in rax `0x3b`, in rdi the address of our string, in rsi `0x0` and in rdx `0x0`. For our rop chain we will need gadgets ending with ret (`pop rip`)of course, so we will need a `pop rax`, `pop rdi`, `pop rsi` and `pop rdx`.
