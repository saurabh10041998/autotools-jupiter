bin_PROGRAMS = jupiter
jupiter_SOURCES = main.c

check_SCRIPTS = greptest.sh
TESTS = $(check_SCRIPTS)

greptest.sh:
	echo './jupiter | grep "Hello from .*jupiter!"' | tee greptest.sh
	chmod +x greptest.sh
