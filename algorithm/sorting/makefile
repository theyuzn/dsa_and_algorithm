CC = gcc
CFLAGS = -Wall -Wextra -Iinc

# Source files directory
SRC_DIR = src

# Object files directory
OBJ_DIR = obj

# Executable file name
EXEC = main

# Source files
SRCS = $(wildcard $(SRC_DIR)/*.c) main.c

# Object files
OBJS = $(patsubst $(SRC_DIR)/%.c, $(OBJ_DIR)/%.o, $(SRCS))


##################################################################
# Add flag for each sorting
##################################################################
ifeq ($(sort),s)
CFLAGS += -DSELECTION
endif

ifeq ($(sort),i)
CFLAGS += -DINSERTION
endif

ifeq ($(sort),q)
CFLAGS += -DQUICK
endif

ifeq ($(sort),qa)
CFLAGS += -DQUICK_API
endif

ifeq ($(sort),b)
CFLAGS += -DBUBBLE
endif

ifeq ($(sort),h)
CFLAGS += -DHEAP
endif

ifeq ($(sort),mr)
CFLAGS += -DMERGE_R
endif

ifeq ($(sort),mi)
CFLAGS += -DMERGE_I
endif

ifeq ($(search),loop)
CFLAGS += -DSEARCH_LOOP
endif
##################################################################

.PHONY: all clean

all: $(EXEC)

# Build executable
$(EXEC): $(OBJS)
	$(CC) $(CFLAGS) $^ -o $@

# Compile source files into object files
$(OBJ_DIR)/%.o: $(SRC_DIR)/%.c | $(OBJ_DIR)
	$(CC) $(CFLAGS) -c $< -o $@

# Compile main.c into object file
$(OBJ_DIR)/main.o: main.c | $(OBJ_DIR)
	$(CC) $(CFLAGS) -c $< -o $@

# Create object files directory
$(OBJ_DIR):
	mkdir -p $(OBJ_DIR)

clean:
	rm -rf $(OBJ_DIR) $(EXEC)
