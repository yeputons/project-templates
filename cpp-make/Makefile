.PHONY: all clean

# Based on https://github.com/yeputons/project-templates

TARGETS=main
SRCS_main=$(wildcard $(SRCDIR)/*.cpp)
BINDIR=.bin
SRCDIR=src
INCDIR=inc

all: $(TARGETS)
main: $(SRCS_main:$(SRCDIR)/%.cpp=$(BINDIR)/%.o)

CXX=g++
CXXFLAGS=-pedantic -Wall -Wshadow -Wextra -Werror -std=c++11 -I$(INCDIR)
LDFLAGS=
LDLIBS=

$(TARGETS):
	$(CXX) -o $@ $(LDFLAGS) $^ $(LDLIBS)

$(BINDIR)/%.o: $(SRCDIR)/%.cpp | $(BINDIR)
	$(CXX) $(CXXFLAGS) -MMD -MP -c -o $@ $<

$(BINDIR):
	mkdir $(BINDIR)

clean:
	rm -rf $(TARGETS) .bin

include $(wildcard $(BINDIR)/*.d)
