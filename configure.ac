#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.71])
AC_INIT([FULL-PACKAGE-NAME], [VERSION], [BUG-REPORT-ADDRESS])
AC_CONFIG_SRCDIR([libhugetlbfs_privutils.h])
AC_CONFIG_HEADERS([config.h])

# Checks for programs.
AC_PROG_CXX
AC_PROG_CC
AC_PROG_INSTALL
AC_PROG_LN_S
AC_PROG_MAKE_SET

# Checks for libraries.
# FIXME: Replace 'main' with a function in '-ldl':
AC_CHECK_LIB([dl], [main])
# FIXME: Replace 'main' with a function in '-lhugetlbfs':
AC_CHECK_LIB([hugetlbfs], [main])
# FIXME: Replace 'main' with a function in '-lhugetlbfs_privutils':
AC_CHECK_LIB([hugetlbfs_privutils], [main])
# FIXME: Replace 'main' with a function in '-lpthread':
AC_CHECK_LIB([pthread], [main])

# Checks for header files.
AC_CHECK_HEADERS([fcntl.h malloc.h mntent.h stdint.h sys/file.h sys/mount.h sys/statfs.h sys/vfs.h unistd.h])

# Checks for typedefs, structures, and compiler characteristics.
AC_CHECK_HEADER_STDBOOL
AC_TYPE_UID_T
AC_C_INLINE
AC_TYPE_MODE_T
AC_TYPE_OFF_T
AC_TYPE_PID_T
AC_TYPE_SIZE_T
AC_TYPE_SSIZE_T
AC_CHECK_TYPES([ptrdiff_t])

# Checks for library functions.
AC_FUNC_ALLOCA
AC_FUNC_CHOWN
AC_FUNC_FORK
AC_FUNC_LSTAT_FOLLOWS_SLASHED_SYMLINK
AC_FUNC_MALLOC
AC_FUNC_MMAP
AC_CHECK_FUNCS([ftruncate gethostname getpagesize memset mkdir munmap rmdir setenv strcasecmp strchr strerror strncasecmp strrchr strstr strtol strtoul strtoull uname])

# glibc 2.34 removed __morecore, so it may not be available with recent versions
# Check glibc __morecore
AC_MSG_CHECKING([if glibc __morecore is available])
AC_COMPILE_IFELSE(
	[AC_LANG_PROGRAM([[
	#include <malloc.h>
	void * morecore_exists() { return &__morecore; }]])],
	[ AC_MSG_RESULT([yes])
       		CFLAGS += -DHAS_MORECORE],
	[ AC_MSG_RESULT([no])]
)

AC_CONFIG_FILES([Makefile
                 tests/Makefile])
AC_OUTPUT
