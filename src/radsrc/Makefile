ifeq (0,$(MAKELEVEL))
$(error Invoke make from the src directory only)
endif
 
# settings inherited from toplevel Makefile
# ---------- end of configurable settings --------------
CPPFLAGS += -Wall -I../libradsrc
.SUFFIXES: .c .cc
.PHONY: clean

OBJS= radsrc.o bins.o outputmci.o useriface.o mcinput.o

radsrc: $(OBJS) ../libradsrc/libradsrc.a
	$(CXX) $(CXXFLAGS) -o radsrc $(OBJS) -L../libradsrc -lradsrc

clean:
	rm -f */*.o core *.core
	rm -f radsrc radsrc.exe

.cc.o:
	$(CXX) -c $(CPPFLAGS) $(CXXFLAGS) $< -o $@

radsrc.o: radsrc.cc useriface.h mcinput.h outputjson.o
outputjson.o: json.hpp
json.hpp:
	wget -c -N https://github.com/nlohmann/json/releases/download/v2.1.1/json.hpp
useriface.o: useriface.cc useriface.h
outputmci.o: outputmci.cc mcinput.h
bins.o: bins.cc bins.h
mcinput.o: mcinput.cc bins.h useriface.h mcinput.h

useriface.h: useroptions.h


