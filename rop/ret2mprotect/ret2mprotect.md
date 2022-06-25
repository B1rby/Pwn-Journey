# Ret2mprotect
### What is ret2mproctect
The mprotect() function is used to change the access protection of a memory mapping to that specified by protection. All whole pages of the process's address space, that were established by the mmap() function, addressed from addr continuing for a length of len will be affected by the change of access protection.Thansk to sys_mprotect we will be able to make the stack executable again.

### Why use the ret2mprotect technique when you can do a ret2libc
First of all, the ret2mprotect function is way easier to use comparing to a ret2libc and can be use wheter the binary is statically linked or dynamically linked. Yeah, if the binary is statically linked you won't be able to do ret2libc since there is no libc which is logic.

### Practice

```c
#include <stdio.h>
#include <string.h>

int main(int argc, char **argv){

    char buffer[260];
    int len, i;
    printf("Welcome in Birby Enterprise\n");
    printf("To join the company, please register with your full name: ");
    gets(buffer);
    len = strlen(buffer);
    printf("Welcome %s in Birby Enterprise\n", buffer);

    return 0;

}
```
##### mprotect
Mprotect requires 3 arguments: 
```c
#include <sys/mman.h>**

int mprotect(void ***_addr_**, size_t** _len_**, int** _prot_**);
```
We need the address of the mapped region, the lenght of memory to change and `0x7 `(PROT_READ|PROT_WRITE|PROT_EXEC). `0x7`, is the value to make the stack readable, writable and executable.
