Our first program

We have to start with something, so we will start with a ridiculously simple program which does nothing but return an error code.

```
/* -- first.s */
/* This is a comment */
.global main /* 'main' is our entry point and must be global */
 
main:          /* This is main */
    mov r0, #2 /* Put a 2 inside the register r0 */
    bx lr      /* Return from main */
```    
Create a file called first.s and write the contents shown above. Save it.

To assemble the file type the following command (write what comes after $ ).

`$ arm-linux-gnueabihf-as -o first.o first.s`
This will create a first.o. Now link this file to get an executable.

`$ arm-linux-gnueabihf-gcc -o first first.o`
If everything goes as expected you will get a first file. This is your program. Run it.

`$ qemu-arm -L /usr/arm-linux-gnueabihf/ ./first`
It should do nothing. Yes, it is a bit disappointing, but it actually does something. Get its error code this time.

`$ qemu-arm -L /usr/arm-linux-gnueabihf/ ./first; echo $?`
2


# Reference
http://thinkingeek.com/2013/01/09/arm-assembler-raspberry-pi-chapter-1/

