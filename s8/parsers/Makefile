CC=$(CROSS_COMPILE)gcc
AR=$(CROSS_COMPILE)ar
CFLAGS=-static -g -Wall -fPIC 

all:

## -c: Compiles without linking.
## -I../: Adds the parent directory to the include path
	$(CC) $(CFLAGS) -c -I../ -I../src binary.c hex.c

# Combines the object files into a static library libparsers.a using ar
# r: Inserts/replaces files in the archive.
	$(AR) r libparsers.a binary.o hex.o

clean:
## Removes all generated files (*.o and libparsers.a).
	rm -f *.o libparsers.a
