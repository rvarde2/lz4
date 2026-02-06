TARGET = tuner

# Compiler and Linker
CC = gcc
LD = gcc

# Directories
SRC_DIR = src
BUILD_DIR = build
LIB_DIR = lib

# Dynamic Library Information
LIBS = -llz4 -lhdr_histogram 
LIB_PATHS = -L$(LIB_DIR)

# Files
SOURCES = $(wildcard $(SRC_DIR)/*.c)
# FIXED: Changed %.cpp to %.c to match your SOURCES
OBJECTS = $(SOURCES:$(SRC_DIR)/%.c=$(BUILD_DIR)/%.o)
# IMPROVED: Standard practice to put the final binary in the build folder
EXEC = $(BUILD_DIR)/$(TARGET)

# Default target
all: $(BUILD_DIR) $(EXEC)

# Ensure the build directory exists even if no compilation happens
$(BUILD_DIR):
	mkdir -p $(BUILD_DIR)

# Link object files into the final binary
$(EXEC): $(OBJECTS)
	$(LD) $(OBJECTS) $(LIB_PATHS) $(LIBS) -o $@

# Compile source files into object files
$(BUILD_DIR)/%.o: $(SRC_DIR)/%.c
	@mkdir -p $(dir $@)
	$(CC) -O3 -DLZ4_MEMORY_USAGE=12 -Wall -c $< -o $@

# Clean up
clean:
	rm -rf $(BUILD_DIR) *.app *.data

.PHONY: all clean
