CC = gcc
CSAPP_INC = ../include
CSAPP_SRC = ../src

CFLAGS = -Wall -g -O2 -I $(CSAPP_INC) -I .
LDLIBS = -lpthread

# Note: we expect compiler warnings when we compile fragments.c
PROGS = fragments.o\
	mmapcopy\
	staticsize\
	dynamicsize\
	sbrk\
	map64\
	map32\
	mallocalign32\
	mallocalign64\

all: $(CSAPP_SRC)/csapp.o $(PROGS)
	(cd malloc; make)

$(PROGS): $(CSAPP_SRC)/csapp.o

$(CSAPP_SRC)/csapp.o: $(CSAPP_SRC)/csapp.c $(CSAPP_INC)/csapp.h

mallocalign32: mallocalign.c
	gcc $(CFLAGS) -m32 -o mallocalign32 mallocalign.c

mallocalign64: mallocalign.c
	gcc $(CFLAGS) -m64 -o mallocalign64 mallocalign.c

map32: map.c 
	gcc $(CFLAGS) -m32 -o map32 map.c

map64: map.c 
	gcc $(CFLAGS) -m64 -o map64 map.c

clean:
	rm -f $(PROGS) *.o *~
	(cd malloc; make clean)

