CFLAGS=-g -Wall
#CC=gcc
CC=arm-cortex_a9-linux-gnueabi-gcc
#AR=ar
AR=arm-cortex_a9-linux-gnueabi-ar
#RANLIB=ranlib
RANLIB=arm-cortex_a9-linux-gnueabi-ranlib
LIBS=-L./ -lcgic

all: libcgic.a cgictest.cgi capture

install: libcgic.a
	cp libcgic.a /usr/local/lib
	cp cgic.h /usr/local/include
	@echo libcgic.a is in /usr/local/lib. cgic.h is in /usr/local/include.

libcgic.a: cgic.o cgic.h
	rm -f libcgic.a
	$(AR) rc libcgic.a cgic.o
	$(RANLIB) libcgic.a

#mingw32 and cygwin users: replace .cgi with .exe

cgictest.cgi: cgictest.o libcgic.a
	$(CC) $(CFLAGS) cgictest.o -o cgictest.cgi ${LIBS}

capture: capture.o libcgic.a
	$(CC) $(CFLAGS) capture.o -o capture ${LIBS}

clean:
	rm -f *.o *.a cgictest.cgi capture

