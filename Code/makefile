#
#  USAGE:
#     make          ... to build the program
#     make test     ... to run the default test case
#     make clean    ... to remove object and executable files
#

# Definitions ... you may need to change these to match your system
CC          = gcc-15
PRE         = ./
OBJ=o
EXE=
RM=rm

CLINKER     = $(CC)
OPTFLAGS    = -std=c11 -fopenmp -O3
LIBS        = -lm
CFLAGS	  = $(OPTFLAGS)

EXES= pi$(EXE) mandel$(EXE)  mm_testbed$(EXE)  linked$(EXE)

MM_OBJS  = mm_testbed.$(OBJ) mm_utils.$(OBJ) mm_ijk.$(OBJ) mm_tst_cases.$(OBJ)

all: $(EXES)

mm_testbed$(EXE): $(MM_OBJS) mm_utils.h
	$(CLINKER) $(CFLAGS) -o mm_testbed$(EXE) $(MM_OBJS) $(LIBS)

linked$(EXE): linked.$(OBJ) 
	$(CLINKER) $(OPTFLAGS) -o linked linked.$(OBJ) $(LIBS)

pi$(EXE): pi.$(OBJ) 
	$(CLINKER) $(OPTFLAGS) -o pi pi.$(OBJ) $(LIBS)

mandel$(EXE):  mandel.$(OBJ) 
	$(CLINKER) $(OPTFLAGS) -o mandel mandel.$(OBJ) $(LIBS)

test: $(EXES)
	$(PRE)pi$(EXE) 
	$(PRE)mandel$(EXE) 
	$(PRE)mm_testbed$(EXE) 
	$(PRE)linked$(EXE) 

clean:
	$(RM) $(EXES) *.$(OBJ)

.SUFFIXES:
.SUFFIXES: .c .cpp .$(OBJ)

.c.$(OBJ):
	$(CC) $(CFLAGS) -c $<

.cpp.$(OBJ):
	$(CC) $(CFLAGS) -c $<
