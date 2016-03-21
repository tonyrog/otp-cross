# Patch needed for gcc-5.0

you need to patch ncurses with the following patch to compile it with latest cross compiler:

    --- ncurses-6.0-20150808+/ncurses/base/MKlib_gen.sh 2015-08-07 00:48:24.000000000 +0000
    +++ ncurses-6.0-20150810/ncurses/base/MKlib_gen.sh  2015-08-10 08:56:39.000000000 +0000
    @@ -2,7 +2,7 @@
    #
    # MKlib_gen.sh -- generate sources from curses.h macro definitions
    #
    -# ($Id: MKlib_gen.sh,v 1.50 2015/08/07 00:48:24 tom Exp $)
    +# ($Id: MKlib_gen.sh,v 1.51 2015/08/10 08:56:39 tom Exp $)
    #
    ##############################################################################
    # Copyright (c) 1998-2014,2015 Free Software Foundation, Inc.                #
    @@ -72,7 +72,7 @@
    # appears in gcc 5.0 and (with modification) in 5.1, making it necessary to
    # determine if we are using gcc, and if so, what version because the proposed
    # solution uses a nonstandard option.
    -PRG=`echo "$1" | $AWK '{ sub(/^[[:space:]]*/,""); sub(/[[:space:]].*$/, ""); print; }' || exit 0`
    +PRG=`echo "$1" | $AWK '{ sub(/^[   ]*/,""); sub(/[     ].*$/, ""); print; }' || exit 0`
    FSF=`"$PRG" --version 2>/dev/null || exit 0 | fgrep "Free Software Foundation" | head -n 1`
    ALL=`"$PRG" -dumpversion 2>/dev/null || exit 0`
    ONE=`echo "$ALL" | sed -e 's/\..*$//'`

