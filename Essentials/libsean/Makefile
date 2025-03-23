# Makefile
#
# Sean16 SOC for iOS
# Meow :3
# Created by SeanIsNotAConstant on October the 12th 2024
#

# config
CF := $(CF) -ISOC -ICompiler

# finding all C and Objective-C files
CFILES := $(shell find . -name "*.c")
MFILES := $(shell find . -name "*.m")

# listing all compiled objects
OBJS := $(patsubst %.c,$(COBJ_DIR)/%.o,$(CFILES)) $(patsubst %.m,$(MOBJ_DIR)/%.o,$(MFILES))

# compiling them to libsean16

all: setup bind

$(COBJ_DIR)/%.o: %.c setup
	@mkdir -p $(dir $@)
	@$(CC) -isysroot $(SDKROOT) $(CF) -ISOC -c $< -o $@

$(MOBJ_DIR)/%.o: %.m setup
	@mkdir -p $(dir $@)
	@$(CC) -isysroot $(SDKROOT) $(CF) -ISOC -c $< -o $@

setup:
	@rm -rf tmp
	@mkdir -p $(COBJ_DIR) $(MOBJ_DIR)
	@mkdir -p tmp/lib

bind: setup $(OBJS)
	@ar rcs tmp/lib/libsean.a $(OBJS)

clean:
	@rm -rf tmp
