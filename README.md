# arm-example

On ubuntu, arm-linux-gnueabi-gcc, arm-linux-gnueabihf-as{gcc,ld...}

# comile
1.static
`arm-linux-gnueabi-gcc hello.c -g -o hello -static`

2.dynmic
`arm-linux-gnueabihf-gcc -o hello-dynmic hello.c`

# run
1.directly
`./hello-dynmic`

2.qemu-arm
`qemu-arm -L /usr/arm-linux-gnueabihf/ ./hello`

# debug
step 1:install gdb-multiarch

`sudo apt-get install gdb-multiarch`

step 2:
`qemu-arm -g 1234 ./hello`

or:
`$ qemu-arm -L /usr/arm-linux-gnueabihf/ -g 1234 ./hello`

step 3:
`$ gdb-multiarch`

`gdb-peda$ set architecture armv5te`

`gdb-peda$ target remote localhost:1234`

`gdb-peda$ file ./hello`

enjoy:
```asm
gdb-peda$ disassemble 
Dump of assembler code for function _start:
=> 0x00008b98 <+0>:	mov	r11, #0
   0x00008b9c <+4>:	mov	lr, #0
   0x00008ba0 <+8>:	pop	{r1}		; (ldr r1, [sp], #4)
   0x00008ba4 <+12>:	mov	r2, sp
   0x00008ba8 <+16>:	push	{r2}		; (str r2, [sp, #-4]!)
   0x00008bac <+20>:	push	{r0}		; (str r0, [sp, #-4]!)
   0x00008bb0 <+24>:	ldr	r12, [pc, #16]	; 0x8bc8 <_start+48>
   0x00008bb4 <+28>:	push	{r12}		; (str r12, [sp, #-4]!)
   0x00008bb8 <+32>:	ldr	r0, [pc, #12]	; 0x8bcc <_start+52>
   0x00008bbc <+36>:	ldr	r3, [pc, #12]	; 0x8bd0 <_start+56>
   0x00008bc0 <+40>:	bl	0x8d2c <__libc_start_main>
   0x00008bc4 <+44>:	bl	0xdf50 <abort>
   0x00008bc8 <+48>:	strdeq	r9, [r0], -r12
   0x00008bcc <+52>:	andeq	r8, r0, r12, lsl #26
   0x00008bd0 <+56>:	andeq	r9, r0, r12, asr r4
End of assembler dump.
```

# Refences
http://thinkingeek.com/arm-assembler-raspberry-pi/

https://www.ece.cmu.edu/~ee349/f-2012/lab2/qemu.pdf

