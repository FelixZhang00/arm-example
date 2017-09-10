Our first program

We have to start with something, so we will start with a ridiculously simple program which does nothing but return an error code.

/* -- first.s */
/* This is a comment */
.global main /* 'main' is our entry point and must be global */
 
main:          /* This is main */
    mov r0, #2 /* Put a 2 inside the register r0 */
    bx lr      /* Return from main */
Create a file called first.s and write the contents shown above. Save it.

To assemble the file type the following command (write what comes after $ ).

$ as -o first.o first.s
This will create a first.o. Now link this file to get an executable.

$ gcc -o first first.o
If everything goes as expected you will get a first file. This is your program. Run it.

$ ./first
It should do nothing. Yes, it is a bit disappointing, but it actually does something. Get its error code this time.

$ ./first ; echo $?
2



