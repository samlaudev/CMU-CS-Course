#CC = /usr/local/cs/bin/gcc
CC = gcc
CFLAGS= -Og -fno-pic
CINC =
F64 =-m64
FNOSP=-fno-stack-protector
FSP=-fstack-protector-all


.SUFFIXES: .c .64s .64d .64ns .64nd

.c.64s:
	$(CC) $(CFLAGS) $(FSP) $(CINC) $(F64) -S $*.c -o $*.64s

.c.64d:
	$(CC) $(CFLAGS) $(FSP) $(CINC) $(F64) $*.c -o $*
	objdump -d $* > $*.64d
	rm -f $*

.c.64ns:
	$(CC) $(CFLAGS) $(FNOSP) $(CINC) $(F64) -S $*.c -o $*.64ns

.c.64nd:
	$(CC) $(CFLAGS) $(FNOSP) $(CINC) $(F64) $*.c -o $*
	objdump -d $* > $*.64nd
	rm -f $*

files:	locate64 bufdemo.64s bufdemo.64d bufdemo.64ns bufdemo.64nd bufdemo-sp bufdemo-nsp hexify smash.txt runaway

locate64: locate.c
	$(CC) $(CFLAGS) $(CINC) $(F64) locate.c -o locate64

runaway: runaway.c
	$(CC) $(CFLAGS) runaway.c -o runaway

hexify: hexify.c
	$(CC) $(CFLAGS) hexify.c -o hexify

bufdemo-sp: bufdemo.c
	$(CC) $(CFLAGS) $(FSP) $(CINC) $(F64) bufdemo.c -o bufdemo-sp

bufdemo-nsp: bufdemo.c
	$(CC) $(CFLAGS) $(FNOSP) $(CINC) $(F64) bufdemo.c -o bufdemo-nsp

# This version assumes that 1) the buffer allocated for echo is 24 (0x18) bytes long, and
# 2) function smash is located at 0x04006fb 
# 2) function smash is located at 0x 40 06 c8
smash.txt: hexify
	./hexify 30 31 32 33 34 35 36 37 38 39 30 31 32 33 34 35 36 37 38 39 30 31 32 33 c8 06 40 > smash.txt

clean:
	rm -f *~ bufdemo-* *.64s *.64d *.64ns *.64nd hexify smash.txt runaway





