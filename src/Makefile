CC = gcc
# ifeq ($(UNAME_S),Darwin)
# 	CC = clang -target arm64-apple-macos11
# endif

# sudo apt install build-essential libpthread-stubs0-dev libudev-dev

CFLAGS = -w -c
LIBS = 
OBJECTS = omapi-main.o omapi-internal.o omapi-download.o omapi-status.o omapi-reader.o omapi-settings.o
INCLUDES = -I../include

ifeq ($(OS),Windows_NT)
	OBJECTS += omapi-devicefinder-win.o
else
	UNAME_R := $(shell uname -r | grep -o Microsoft)
	ifeq ($(UNAME_R),Microsoft)
		# WSL Not supported
		OBJECTS += omapi-devicefinder-linux.o
		LIBS += -lpthread -ludev
	else
		UNAME_S := $(shell uname -s)
		ifeq ($(UNAME_S),Linux)
			OBJECTS += omapi-devicefinder-linux.o
			LIBS += -lpthread -ludev
		endif
		ifeq ($(UNAME_S),Darwin)
			OBJECTS += omapi-devicefinder-mac.o
			LIBS += -lpthread -framework Cocoa -framework IOKit -framework DiskArbitration
		endif
	endif
endif

.PHONY: default

default: libomapi.a

all: libomapi.a

libomapi.dylib : libomapi.a
	$(CC) -dynamiclib -o libomapi.dylib libomapi.a

libomapi.dll : libomapi.a
	$(CC) -shared -o libomapi.dll libomapi.a

libomapi.so : libomapi.a
	$(CC) -shared -o libomapi.so libomapi.a

libomapi.a : $(OBJECTS)
	ar rcs libomapi.a $(OBJECTS)
	# lipo -info libomapi.a

omapi-main.o : omapi-main.c
	$(CC) $(CFLAGS) $(INCLUDES) -c omapi-main.c

omapi-internal.o : omapi-internal.c
	$(CC) $(CFLAGS) $(INCLUDES) -c omapi-internal.c

omapi-download.o : omapi-download.c
	$(CC) $(CFLAGS) $(INCLUDES) -c omapi-download.c

omapi-status.o : omapi-status.c
	$(CC) $(CFLAGS) $(INCLUDES) -c omapi-status.c

omapi-reader.o : omapi-reader.c
	$(CC) $(CFLAGS) $(INCLUDES) -c omapi-reader.c

omapi-settings.o : omapi-settings.c
	$(CC) $(CFLAGS) $(INCLUDES) -c omapi-settings.c

omapi-devicefinder-linux.o : omapi-devicefinder-linux.c
	$(CC) $(CFLAGS) $(INCLUDES) -c omapi-devicefinder-linux.c

omapi-devicefinder-mac.o : omapi-devicefinder-mac.c
	$(CC) $(CFLAGS) $(INCLUDES) -c omapi-devicefinder-mac.c

omapi-devicefinder-win.o : omapi-devicefinder-win.cpp
	$(CC) $(CFLAGS) $(INCLUDES) -c omapi-devicefinder-win.cpp

clean:
	rm -f *.o libomapi.a libomapi.so libomapi.dylib libomapi.dll

