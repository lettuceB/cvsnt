## Process this file with automake to produce Makefile.in
# Makefile for library files used by GNU CVS.
# Copyright (C) 1986, 1988-1994, 2000 Free Software Foundation, Inc.

# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2, or (at your option)
# any later version.

# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.

# For now we need to include $(top_srcdir)/src because some systems
# (at least 'AIX rioscpu2 3 4 000030498200',
# 'HP-UX hp60 B.10.20 A 9000/770 hp60 two-user license', &
# 'IRIX64 sgiop110 6.5 07151433 IP30') have trouble finding error.h
# when compiling savecwd.c
#
# FIXME - the fact that compiling on my Linux 2.2.16 system finds
# /usr/include/error.h instead of $(top_srcdir)/src/error.h but
# everything compiles and tests anyhow implies that src/error.h may
# be unecessary now.  Should look more deeply into this
#
# $(includeopt) is CVS specific and set by configure
AM_CPPFLAGS = -I$(top_srcdir)/src $(includeopt)
AM_CFLAGS = -DCVS_CONFIG_DIR=\"$(cvs_config_dir)\" -DCVS_LIBRARY_DIR=\"$(cvs_library_dir)\"


noinst_LIBRARIES = libcvs.a

# Always use CVS's regular expression matcher regex.o, because of
# variations in regular expression syntax - we want to be the same
# across systems and (probably) compared with old versions of CVS too.
#
# On a more mundane/detail level, having regex.h match regex.c can be
# an issue if we aren't careful.
#
# Also should look into unifying regular expression matching in CVS
# with the diff library (perhaps to have the caller, CVS, do the
# matching?)
libcvs_a_SOURCES = \
	argmatch.c \
	getpass.c \
	sighandle.c \
	getpass.h \
	fnmatch.h \
	md5.h \
	savecwd.h \
	system.h \
	wait.h \
	xselect.h \
	xtime.h
libcvs_a_LIBADD = @LIBOBJS@

EXTRA_DIST = \
	.cvsignore \
	ChangeLog.fsf \
	build_lib.com \
	xgssapi.h

# for backwards compatibility with the old makefiles
realclean: maintainer-clean
.PHONY: realclean
