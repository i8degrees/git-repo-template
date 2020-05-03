OS_TAG := $(shell uname -s)

# It is likely that default C compiler is already gcc, but explicitly
# set, just to be sure
CC = clang

# The CFLAGS variable sets compile flags for gcc:
#  -g        compile with debug information
#  -Wall     give verbose compiler warnings
#  -O0       do not optimize generated code
#  -std=c99  use the C99 standard language definition
CFLAGS = $(shell pkg-config --cflags libnotify)

# The LDFLAGS variable sets flags for linker
#  -lm   says to link in libm (the math library)
LDFLAGS = $(shell pkg-config --libs libnotify)

# In this section, you list the files that are part of the project.
# If you add/change names of source files, here is where you
# edit the Makefile.
SOURCES = main.c
OBJECTS = $(SOURCES:.c=.o)
TARGET = main

# The first target defined in the makefile is the one
# used when make is invoked with no argument. Given the definitions
# above, this Makefile file will build the one named TARGET and
# assume that it depends on all the named OBJECTS files.

$(TARGET) : $(OBJECTS)
  $(CC) $(CFLAGS) -o $@ $^ $(LDFLAGS)

all: $(OS_TAG)
  @echo "INFO: Compiling and linking main stub for ${OS_TAG}..."

# Phony means not a "real" target, it doesn't build anything
# The phony target "clean" is used to remove all compiled object files.

.PHONY: clean

clean:
  @rm -f $(TARGET) $(OBJECTS) core
