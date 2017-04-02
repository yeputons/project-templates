.PHONY: all clean

TARGET=main
BINDIR=.bin
SRCDIR=src
INCDIR=inc

CXX=g++
CXXFLAGS=-pedantic -Wall -Wshadow -Wextra -Werror -std=c++11 -I$(INCDIR)
LDFLAGS=
LDLIBS=

SRCS=$(wildcard $(SRCDIR)/*.cpp)
OBJS=$(SRCS:$(SRCDIR)/%.cpp=$(BINDIR)/%.o)

all: $(TARGET)

$(TARGET): $(OBJS)
	$(CXX) -o $@ $(LDFLAGS) $(OBJS) $(LDLIBS)

$(BINDIR)/%.o: $(SRCDIR)/%.cpp | $(BINDIR)
	$(CXX) $(CXXFLAGS) -MMD -MP -c -o $@ $<

$(BINDIR):
	mkdir $(BINDIR)

clean:
	rm -rf $(TARGET) .bin

include $(wildcard $(BINDIR)/*.d)
