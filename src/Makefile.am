bin_PROGRAMS = jupiter
jupiter_SOURCES = main.c
jupiter_CPPFLAGS = -I$(top_srcdir)/common
jupiter_LDADD = ../common/libjupcommon.a

check_SCRIPTS = greptest.sh
TESTS = $(check_SCRIPTS)

greptest.sh:
	echo './jupiter | grep "Hello from .*jupiter!"' | tee greptest.sh
	chmod +x greptest.sh
