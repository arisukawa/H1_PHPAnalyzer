# A prototype Makefile for H1
#
# last update: $Date: 2010/10/08 13:39:31 $
# by         : $Author: msteder $
#
# The name of this module
MODULENAME = H1Examples
#
# macro definitions
# DEFINES = 
#
# debug on or off (comment next line to disable debugger information)
DEBUG = -g 
#
# The shared library to make (if any): e.g. libH1Tracks.so
#SLIB_TARGETS =  libTrackAnalysis
SLIB = libTrackAnalysis.so
#
# The static library to make (if any): e.g. libH1Tracks.a
# LIB_TARGETS = 
#LIB =
# #
# The binaries you would like to make, you have to provide the final linking
BIN = TrackAnalysis TrackAnalysisODS

#ifeq ($(STANDALONE),yes)
  # no rerun_rec
#else
#  BIN += rerun_rec 
#endif

#
# Objects you need for the libraries
OBJS += TriggerBranches.o VertexBranches.o EnergyFlowBranches.o \
	TrackBranches.o

# OBJS += UserEvent.o UserFiller.o

# Dictionary objects, default is: DICTOBJS = $(OBJS:.o=Dict.o)

# Now your special libs and includes
# EXTRA_INCLUDEDIRS = ~/my_favourite_library/include
# EXTRA_LIBDIRS = ~/my_favourite_library/lib
# EXTRA_LINKFLAGS = -lmy_favourite_library
# Dummy objects
# DUMMYOBJS =

# Dummy dictionary objects
# DUMMYDICTOBJS = $(DUMMYOBJS:.o=Dict.o)

#extra files to be removed when calling 'make clean' or 'make clobber'
#EXTRA_CLEAN_RULES=
#EXTRA_DISTCLEAN_RULES=

# defines LIBS
# defines Rules for .c .C .cpp .f Dict.C .so
ifeq ($(H1BASICMK),local)
  include  ../oo_tools/H1Basic.mk
else
  include  $(H1DIST)/releases/$(H1CURRENT)/oo_tools/H1Basic.mk
endif                                                             

# include the dependencies if created via 'make depend'
-include Makefile.dep


# the executables


TrackAnalysis: outputdirs $(BUILDDIR)/TrackAnalysis.o slib
	@echo ""
	@echo Linking test program for mods access: $@ ...
	$(LOADER) \
	$(BUILDDIR)/TrackAnalysis.o -lTrackAnalysis \
	$(OO_LIBS) \
	-lH1Tools -lH1Arrays -lH1Hat -lH1Mods -lH1Geom -lH1Skeleton \
	-lH1HadronicCalibration \
	-lH1OOBanks -lH1Pointers -lH1Skeleton -lH1Steering \
	-lH1Tracks -lH1PhysUtils -lH1JetFinder -lH1Finder -lH1Clusters \
	\
	$(ROOTLIBS) -lEG -l${FORTRANLIB} \
	\
	-o $(BINDIR)/TrackAnalysis
	@echo $@ created ...
	@echo ""

TrackAnalysisODS: outputdirs $(BUILDDIR)/TrackAnalysis.o slib
	@echo ""
	@echo Linking test program for ods access: $@ ...
	$(LOADER) \
	$(BUILDDIR)/TrackAnalysis.o -lTrackAnalysis \
	$(OO_LIBS) \
	-lH1Tools -lH1Arrays -lH1Hat -lH1Mods \
	-lH1Ods -lH1MagfieldOO \
	-lH1Geom -lH1Skeleton \
	-lH1HadronicCalibration \
	-lH1OOBanks -lH1Pointers -lH1Skeleton  \
	-lH1Steering \
	-lH1Tracks -lH1PhysUtils  -lH1JetFinder -lH1Finder -lH1Clusters \
	\
	$(ROOTLIBS) -lEG -l${FORTRANLIB} \
	-Wl,-rpath=../lib/amd64_rhel60 \
	-o $(BINDIR)/TrackAnalysisODS
	@echo $@ created ...
	@echo ""

#	-lH1TrkFinder -lH1HfsFinder -lH1MuonFinder \
#	-lH1PartEmFinder -lH1Selection -lH1SubDetInfo -lH1ElecCalibration \
#	-lH1SoftLeptonId \


#	-L/afs/desy.de/group/h1/h1/lib -lh1rec -lh1sim  -lh1trig -lh1mcutil -lh1ndb -llook  -lh1util \
#	-L/nfs/dust/h1/group/sschmitt/h1_analysis/lib/amd64_rhel60 -lfpackOO -lbos \
#	-L /afs/desy.de/group/h1/h1/lib/cern/2005/lib -lmathlib -lpacklib -lkernlib \

#	-lH1Filler_odsonly -lH1MagfieldOO \

#	$(ROOTLIBS) -lEG -L../fpack/Linux/lib -lfpack10616 -l${FORTRANLIB} \
