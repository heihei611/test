CC = g++
VS_ROOT  = .
SRCS  = $(wildcard $(VS_ROOT)/*.cpp)
OBJS := $(SRCS:%.cpp=%.o)
INCLUDE = -I ./:../../include

$(warning  $(INCLUDE))

LDLIBS = -lHCUSBSDK -lpthread
LIBPATH = ../../library/linux64

# If no configuration is specified, "Debug" will be used
ifndef CFG
CFG=Debug
endif

ifeq "$(CFG)" "Debug"
OUTFILE = usb_demo
CFLAGS = -g -o0 -Wall
else
OUTFILE = usb_demo
CFLAGS = -o0 -Wall  
endif

COMPILE = $(CC) $(CFLAGS) $(INCLUDE) -c "$<" -o "$@" 
LINK = $(CC) $(CFLAGS) $(OBJS) -o $(OUTFILE) -L$(LIBPATH) $(LDLIBS) -Wl,-rpath=./:$(LIBPATH)

all:$(OUTFILE)
	@echo "Build usb_demo Finished"
	mv $(OUTFILE) $(LIBPATH)

$(OUTFILE):$(OBJS)
	$(LINK)

%.o:%.cpp
	$(COMPILE)



clean:
	rm -f $(OBJS)
	rm -f $(LIBPATH)/$(OUTFILE)
	
	
