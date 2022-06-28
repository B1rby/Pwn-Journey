## Baby Overflow

The source code is available [here](https://github.com/seal9055/PWN_Zero2Hero/blob/main/stack_challenges/01_baby_overflow/vuln.c).

### Security

![image](https://user-images.githubusercontent.com/87600765/176226140-1839dfd7-6cdf-4984-b2a5-bf23bcdc696e.png)

As you can see PIE, NX and RELRO is enabled. Also ASLR is enabled.

![image](https://user-images.githubusercontent.com/87600765/176226476-6c7e3652-572d-43ee-a1f7-baad19bc3bf4.png)

In this case ASLR and NX will be enable. Address space layout randomization (ASLR) is a computer security technique involved in preventing exploitation of memory corruption vulnerabilities. In order to prevent an attacker from reliably jumping to, for example, a particular exploited function in memory, ASLR randomly arranges the address space positions of key data areas of a process, including the base of the executable and the positions of the stack, heap and libraries. Since there is NX the stack isn't executable (`rw`) and PIE binary  makes all of its dependencies are loaded into random locations within virtual memory each time the application is executed.
