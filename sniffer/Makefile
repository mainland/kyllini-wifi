WIFITOP=..

TESTS=$(shell ls *.outfile.ground | sort)

.PHONY : all
all : $(patsubst %.outfile.ground, %.test, $(TESTS))

include $(WIFITOP)/mk/common.mk

.PHONY : clean
clean :
	$(_QUIET)rm -f \
	      $(patsubst %.outfile.ground, %.c, $(TESTS)) \
	      $(patsubst %.outfile.ground, %.exe, $(TESTS)) \
	      $(patsubst %.outfile.ground, %.outfile, $(TESTS)) \
	      $(patsubst %.outfile.ground, %.dump*, $(TESTS))

# We remove -p (ignore endings) from tests to detect subtle errors For example,
# if no packet is detected, there is no output, and -p treats that as correct
%_test.test : %_test.outfile %_test.outfile.ground
	@echo "Comparing output for" $*
	$(_QUIET)$(BLINKDIFF) -f $< -g $<.ground -d -v -n 0.9
