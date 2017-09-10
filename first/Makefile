GCC=arm-linux-gnueabihf-gcc
AS=arm-linux-gnueabihf-as
RUN=qemu-arm -L /usr/arm-linux-gnueabihf/


all: first

first: first.o
				$(GCC) -g -o $@ $<

first.o : first.s
					$(AS) -o $@ $< 

run: first
	$(RUN) ./first

clean:
			rm -vf first *.o	
