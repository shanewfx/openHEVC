include ../../config.mak

vpath %.c $(SRC_PATH)/modules/openhevc_dec

CFLAGS=$(OPTFLAGS) $(OHEVC_CFLAGS) $(SDL_CFLAGS) -I"$(SRC_PATH)/include"

ifeq ($(DEBUGBUILD), yes)
CFLAGS+=-g
LDFLAGS+=-g
endif

ifeq ($(GPROFBUILD), yes)
CFLAGS+=-pg
LDFLAGS+=-pg
endif

EXTRALIBS+= -L../../bin/gcc -lgpac $(OHEVC_LDFLAGS) $(SDL_LIBS)

#common obj
OBJS= openhevc_dec.o

SRCS := $(OBJS:.o=.c) 

LIB=gm_openhevc_dec.$(DYN_LIB_SUFFIX)


all: $(LIB)


$(LIB): $(OBJS)
	$(CC) $(SHFLAGS) $(LDFLAGS) -o ../../bin/gcc/$@ $(OBJS) $(EXTRALIBS)

clean: 
	rm -f $(OBJS) ../../bin/gcc/$(LIB)

dep: depend

depend:
	rm -f .depend	
	$(CC) -MM $(CFLAGS) $(SRCS) 1>.depend

distclean: clean
	rm -f Makefile.bak .depend



# include dependency files if they exist
#
ifneq ($(wildcard .depend),)
include .depend
endif
