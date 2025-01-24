# **************************************************************************** #
#                                                                              #
#                                                         :::      ::::::::    #
#    Makefile                                           :+:      :+:    :+:    #
#                                                     +:+ +:+         +:+      #
#    By: jyao <jyao@student.42abudhabi.ae>          +#+  +:+       +#+         #
#                                                 +#+#+#+#+#+   +#+            #
#    Created: 2025/01/24 14:44:37 by jyao              #+#    #+#              #
#    Updated: 2025/01/24 14:54:28 by jyao             ###   ########.fr        #
#                                                                              #
# **************************************************************************** #

# Compiler to use (e.g., gcc)
CC := gcc
# Compiler flags
CFLAGS := -Wall -Wextra -Werror -g
# Linker flags
LDFLAGS :=
# Directory for source files
SRC_DIR = src
# Directory for header files
INC_DIR = include
# Directory for build files
BUILD_DIR = build
# Directory for the executable
BIN_DIR = bin

# Find all the .c files in the src directory
SRC_FILES = $(wildcard $(SRC_DIR)/*.c)

# Object files (compiled .o files)
OBJ_FILES = $(SRC_FILES:$(SRC_DIR)/%.c=$(BUILD_DIR)/%.o)

# Final executable name
TARGET = $(BIN_DIR)/sniffer

.PHONY: all clean fclean re

# Default target to build
all: $(TARGET)

# Rule for compiling .c to .o (object) files
$(BUILD_DIR)/%.o: $(SRC_DIR)/%.c
	$(CC) $(CFLAGS) -I$(INC_DIR) -c $< -o $@

# Linking rule to create the final executable
$(TARGET): $(OBJ_FILES)
	$(CC) $(OBJ_FILES) -o $@ $(LDFLAGS)

# Clean up build artifacts
clean:
	rm -rf $(OBJ_FILES)

fclean: clean
	rm -rf $(TARGET)

# Rebuild everything
re: fclean all

