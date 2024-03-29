## Pwn Journey

Assembly:
- https://chromium.googlesource.com/chromiumos/docs/+/master/constants/syscalls.md#x86_64-64_bit
- https://en.wikibooks.org/wiki/X86_Assembly/X86_Architecture
- https://cs.lmu.edu/~ray/notes/nasmtutorial/
- https://www.nasm.us/xdoc/2.15.05/html/nasmdoc0.html
- https://guyinatuxedo.github.io/01-intro_assembly/assembly/index.html
- https://www.youtube.com/watch?v=VQAKkuLL31g&list=PLetF-YjXm-sCH6FrTz4AQhfH6INDQvQSn
- https://www.tutorialspoint.com/assembly_programming/assembly_introduction.htm
- https://riptutorial.com/assembly
- https://www.intel.com/content/dam/www/public/us/en/documents/manuals/64-ia-32-architectures-software-developer-instruction-set-reference-manual-325383.pdf

C (GNU linux system):
- [Compilation](https://github.com/B1rby/Pwn-Journey/blob/main/C/compilation.md)
- [Pointers in c and Assembly and Memory overview in depth ](https://github.com/B1rby/Pwn-Journey/blob/main/C/pointers.md)

Rop techniques to bypass mitigations:

- [ret2mprotect call sys_mprotect (NX)](https://github.com/B1rby/Art-of-Exploitation/blob/main/rop/ret2mprotect/ret2mprotect.md)
- [ret2libc (NX)](https://github.com/B1rby/Art-of-Exploitation/blob/main/rop/ret2libc/ret2libc.md)
- [call sys_execve with /bin/sh argument (NX and ASLR)](https://github.com/B1rby/Art-of-Exploitation/blob/main/rop/sys_execve/call%20sys_execve.md)
   
Copyright © Birby 2022. The [Pwn Journey](https://github.com/B1rby/Pwn-Journey) by [B1rby](https://github.com/B1rby) is licensed under a [Creative Commons Attribution-NonCommercial 4.0 International License](https://creativecommons.org/licenses/by-nc/4.0/).
