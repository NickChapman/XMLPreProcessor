SRC = XMLConfDocument XMLConfParser XMLConfWriter
OBJ = $(addsuffix .o,$(SRC))

INC = -I/usr/include/libxml2
LIB = -lxml2

#CFLAGS	 = -O -fPIC -g3 -Wall -Wextra -m32
CFLAGS	 = -O -fPIC -g3 -Wall -Wextra
SOFLAGS	 = -shared
CC	 = g++
CCC	 = gcc

all: libxmlpreprocessor.so libxmlpreprocessor.a

# Tool invocations
%.o: %.cpp %.h
	$(CC) -o $@ -c $< $(CFLAGS) $(INC) 
	
UNAME_S := $(shell uname -s)
ifeq ($(UNAME_S), Darwin)
libxmlpreprocessor.so: $(OBJ)
	$(CC) $(SOFLAGS) -Wl,-install_name,$@ -o $@ $^ $(CFLAGS) $(LIB)
else
libxmlpreprocessor.so: $(OBJ)
	$(CC) $(SOFLAGS) -Wl,-soname,$@ -o $@ $^ $(CFLAGS) $(LIB)
endif

libxmlpreprocessor.a: $(OBJ)
	ar rvs $@ $^

# Other Targets
clean:
	rm -rf *.so
	rm -rf *.a
	rm -rf *.o

.PHONY: all clean dependents
.SECONDARY:

