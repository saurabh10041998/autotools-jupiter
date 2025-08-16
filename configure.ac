AC_PREREQ([2.69])
AC_INIT([jupiter], [0.1], [jupiter-bugs@example.com])
AM_INIT_AUTOMAKE
AC_CONFIG_HEADERS([config.h])
AC_CONFIG_SRCDIR([src/main.c])

# Check for programs
AC_PROG_CC
AC_PROG_INSTALL

# Check for headers
AC_CHECK_HEADERS([stdlib.h pthread.h])

# Check for feature flag
AC_ARG_ENABLE([async-exec],
    [AS_HELP_STRING([--disable-async-exec],
        [disable async execution @<:@default no@:>@])],
        [async_exec=${enableval}], [async_exec=yes])


if test "x${async_exec}" = xyes; then
    have_pthreads=no
    AC_SEARCH_LIBS([pthread_create], [pthread], [have_pthreads=yes])

    if test "x${have_pthreads}" = xyes; then
        AC_CHECK_HEADERS([pthread.h], [], [have_pthread=no])
    fi

    if test "x${have_pthreads}" = xno; then
        AC_MSG_WARN([
    ----------------------------------------------
    Unable to find pthreads on this system
    Building a single threaded version
    ----------------------------------------------])
        async_exec=no
    fi
fi

if test "x${async_exec}" = xyes; then
    AC_DEFINE([ASYNC_EXEC], [1], [async execution enabled])
fi

# check for libraries

# check for typedefs

# check for library functions
AC_CONFIG_FILES([Makefile
                src/Makefile])

AC_OUTPUT

cat << EOF
-------------------------------------------------------------
${PACKAGE_NAME} Version ${PACKAGE_VERSION}

Prefix: '${prefix}'
Compiler: '${CC} ${CFLAGS} ${CPPFLAGS}'

Package Feature:
    Async Execution: ${async_exec}

Now type 'make @<:@<target>@:>@'
Where optional <target> is
    all - builds all binaries
    install - install everything

-------------------------------------------------------------
EOF