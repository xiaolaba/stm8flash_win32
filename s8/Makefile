## xiao_laba_cn@yahoo.commands
## Makefile revised, only for win32

CC=$(CROSS_COMPILE)gcc

CFLAGS=-static -g -Wall -fPIC
INCLUDES=-I./parsers -I./src -I.
LDFLAGS=-static -g -fPIC -lparsers -lm
LIBRARIES=-L$(ROOTDIR)/lib -L./parsers

# Source files
SRC_DIR = src


# Source files list (without paths)
SRC_FILES = main.c utils.c stm8.c e_w_routines.c serial_common.c serial_platform.c

# Add src/ prefix to sources
SOURCES = $(addprefix src/,$(SRC_FILES))

#SOURCES=$(wildcard $(SRC_DIR)/*.c)
OBJECTS=$(patsubst $(SRC_DIR)/%.c,obj/%.o,$(SOURCES))




# Output directories
OUT_DIR=win_exe
OBJ_DIR=obj

# Ensure directories exist
$(shell mkdir -p $(OUT_DIR) $(OBJ_DIR))

TARGET = $(OUT_DIR)/s8

all: lib_parsers $(TARGET)

$(TARGET): $(OBJECTS)
	$(CC) $(OBJECTS) $(LIBRARIES) $(LDFLAGS) -o $@

lib_parsers:
	$(MAKE) -C parsers

$(OBJ_DIR)/%.o: $(SRC_DIR)/%.c
	$(CC) -c $(CFLAGS) $(INCLUDES) $< -o $@

clean:
	rm -rf $(OBJ_DIR)/*.o
	rm -f $(TARGET)
	$(MAKE) -C parsers clean

romfs:
	# Your romfs commands here