# the compiler: gcc for C program, define as g++ for C++
CC = gcc

# compiler flags:
#  -g    adds debugging information to the executable file
#  -Wall turns on most, but not all, compiler warnings
CFLAGS  = -g -Wall

LIBS = -lpcap

# the build target executable:
TARGET = main

all: $(TARGET)

$(TARGET): $(TARGET).c
	$(CC) $(CFLAGS) -o $(TARGET) $(TARGET).c $(LIBS)

install:
	mkdir -p /etc/systemd/system
	cp olan-libpcap*.service /etc/systemd/system/
	cp olan-libpcap*.conf /etc/
	mkdir -p /var/log/libpcap_echo_server/

uninstall:
	rm -rfv /etc/systemd/system/olan-libpcap-*.service
	rm -rfv /etc/systemd/system/olan-libpcap*.conf
	rm -rfv /var/log/libpcap_echo_server/

clean:
	$(RM) $(TARGET)