TOP=../../../..
WIFITOP=../..

KZCLIB=$(WIFITOP)/lib

TESTS=$(shell ls *.blk | sort)

.PHONY : all
all : $(patsubst %.blk, %.perf, $(TESTS))

include $(WIFITOP)/mk/perf.mk
