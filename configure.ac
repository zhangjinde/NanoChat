AC_PREREQ([2.69])
AC_INIT([nanochat], [0.1], [hamidreza.s@gmail.com])
AM_INIT_AUTOMAKE([foreign])

NANOMSG_VERSION=0.8-beta
AC_SUBST([NANOMSG_VERSION])

VEDIS_VERSION=1.2.6
AC_SUBST([VEDIS_VERSION])

SODIUM_VERSION=1.0.9
AC_SUBST([SODIUM_VERSION])

PARSON_VERSION=1.0.0
AC_SUBST([PARSON_VERSION])

BASE64_VERSION=1.0.0
AC_SUBST([BASE64_VERSION])

AC_PROG_CC
AC_LANG([C])

AC_HEADER_STDC
AC_CHECK_HEADERS([stdio.h stdlib.h unistd.h getopt.h string.h time.h \
                  sys/select.h stdarg.h pthread.h pwd.h sys/socket.h \
                  arpa/inet.h ifaddrs.h])

AC_TYPE_SIZE_T
AC_CONFIG_FILES([lib/nanomsg/Makefile \
                 lib/vedis/Makefile \
		 lib/sodium/Makefile \
		 lib/parson/Makefile \
                 lib/base64/Makefile \
                 src/Makefile \
		 Makefile])

AC_CANONICAL_HOST
case "${host_os}" in
    *linux*)
        # Define on Linux to enable all library features
	NC_OS_SPECIFIC_LDADD="-l:libnanomsg.a -l:libvedis.a -l:libsodium.a -l:libparson.a -l:libbase64.a"
	NC_EXTRA_LDADD=-lanl 
        ;;
    *freebsd*)
        # Define on FreeBSD to enable all library features
	NC_OS_SPECIFIC_LDADD="-lnanomsg -lvedis -lsodium -lparson -lbase64"
	NC_EXTRA_LDADD=
        ;;
    *darwin*)
        # Define on Darwin to enable all library features
	NC_OS_SPECIFIC_LDADD="-lnanomsg -lvedis -lsodium -lparson -lbase64"
	NC_EXTRA_LDADD=
        ;;
    *)
        AC_MSG_ERROR([unsupported system: ${host_os}.])
        ;;
esac
AC_SUBST([NC_OS_SPECIFIC_LDADD])
AC_SUBST([NC_EXTRA_LDADD])

AC_OUTPUT
