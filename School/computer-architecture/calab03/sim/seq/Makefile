# Modify this line to indicate the default version

VERSION=std

# Modify these two lines to choose your compiler and compile time
# flags.

CC=gcc
CFLAGS=-Wall -O2

##################################################
# You shouldn't need to modify anything below here
##################################################

MISCDIR=../misc
HCL2C=$(MISCDIR)/hcl2c
INC=$(TKINC) -I$(MISCDIR) $(GUIMODE)
LIBS=$(TKLIBS) -lm
YAS=../misc/yas

all: ssim

# This rule builds the SEQ simulator (ssim)
ssim: seq-$(VERSION).hcl ssim.c  sim.h $(MISCDIR)/isa.c $(MISCDIR)/isa.h
	# Building the seq-$(VERSION).hcl version of SEQ
	$(HCL2C) -n seq-$(VERSION).hcl <seq-$(VERSION).hcl >seq-$(VERSION).c
	$(CC) $(CFLAGS) $(INC) -o ssim \
		seq-$(VERSION).c ssim.c $(MISCDIR)/isa.c $(LIBS)

# These are implicit rules for assembling .yo files from .ys files.
.SUFFIXES: .ys .yo
.ys.yo:
	$(YAS) $*.ys


clean:
	rm -f ssim seq*-*.c *.o *~ *.exe *.yo *.ys




