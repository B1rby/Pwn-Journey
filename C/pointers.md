# Pointers in C and Assembly and How works memory
## Chapter 1 Pointers in C
### Part 1 Pointers in Assembly

In Assembly, we can treat our registers as pointers and for this, the syntax is really simple. Pointers in assembly are really simple. It's when you register contain
an existing address in memory and that this address is pointing to some value. Let's take a look at a simple NASM (Netwide Assembler) Program.

### Part 2 Introduction to pointers in C

Below, is a really simple representation of the computer memory or more specifically the Random Access Memory or RAM. This is the memory that we talk about in the 
context of program execution. 

![image](https://user-images.githubusercontent.com/87600765/184961364-e45f88ee-f84d-42d7-8577-88b37f4f94f5.png)

Let's say that each segment of this scheme is 1 byte. Each byte has this memory address. The address at the bottom is the lowest memory address. and this address 
will increase while we go up. Lets say that the address of the first segment `from the bottom` is 0x1. it means that the second address will be 0x2 etc. During the 
program execution you may declare some variables like this for example.

```c
int main(){
    int a;
    int b;
    return 0;
}
```

Well you can try to find the address of the variable but you won't find it. Why ? because your compiler is smart and know how to optimize  your program. Since you are not using the
variable a and b and that you didn't initialize them they won't exist. So remember if you declare variables like this but that you are not using there won't have memory 
allocated for these variables. 

But if it's not the case, well 4 bytes will be allocated on the stack since it's an integer and the value will be assigned to it. For example let's consider this program.
```c
int main(){
    int a = 23;
    int b = 14;
    char c = 'A';
    return 0;
}
```
This time the variables will be on the stack so space will be allocated for them. Let's take look to the assembly code used for initialized them.

```nasm
mov DWORD PTR [rbp-0x8], 0x17
mov DWORD PTR [rbp-0x4], 0xe
mov BYTE PTR [rbp-0x9], 0x41
``` 

Well the code is simple. The first line simply
say to move the value of 0x17 (23 in hex)
in the memory location pointed to by the address of
rbp-8. And the seconde line move the value of
0xe (14 in hex) in the memory location pointed to by 
the address of rbp-4.  And the third line
move one bytes which is 0x41 (A in hex) in the
memory location pointed to by rbp-9. But why 9. Well 
We initialize 2 integers so 4 + 4 = 8 bytes. 
And we initialize one char so its 1 byte. So we
allocated 9 bytes. As you see when the initialization is done
they specify the size of our variable. Since integers are 4 bytes
it's gonna use the `DWORD PTR []` syntax to use only 4 bytes because
a double word is 32 bits so 4 bytes. For the character since the size is only 8 bits so 1 bytes it's specify the size and use `BYTE PTR`.

You may be wondering why I have put 0xe at 
the bottom of the stack so at the higher
address where as 0xe is initialize to b after
0x17 is initialize to A. Well it's because 
a has a higher value than b. So because of 
my GCC (it mays not be the same for you)
the stack will put the lower value to the higher 
address.  This is because of memory alignment
for optimization but we won't talk about this
in this blog. 

And since the stack grows down it's 
gonna put 0x17 at the address-4 from the 
address of 0xe. 
