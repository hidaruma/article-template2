AC_PREREQ([2.69])
AC_INIT(article-template2, 1.0, hidaruma@outlook.jp)

AC_CHECK_PROG(PLATEX, platex, platex)
AC_CHECK_PROG(LUALATEX, lualatex, lualatex)
AC_CHECK_PROG(XELATEX, xelatex, xelatex)


AC_ARG_ENABLE([luatex],
  AS_HELP_STRING([--enable-luatex],
    [enable the use of luatex]),
  [ENABLE_LUATEX=true],
  [ENABLE_LUATEX=false]
)

AC_ARG_ENABLE([xetex],
  AS_HELP_STRING([--enable-xetex],
    [enable the use of xetex]),
  [ENABLE_XETEX=true],
  [ENABLE_XETEX=false]
)

AC_ARG_ENABLE([ptex],
  AS_HELP_STRING([--enable-ptex],
    [enable the use of ptex]),
  [ENABLE_PTEX=true],
  [ENABLE_PTEX=false]
)


if test "$ENABLE_LUATEX" = "true" ; then
if test -z "$LUALATEX"; then
  AC_MSG_ERROR([Unable to use LuaLaTeX])
fi
fi

if  test "$ENABLE_XETEX" = "true" ;then
 if test -z "$XELATEX"; then
  AC_MSG_ERROR([Unable to use XeLaTeX])
fi
fi

if  test "$ENABLE_PTEX" = "true" ;then
if test -z "$PLATEX"; then
  AC_MSG_ERROR([Unable to use pLaTeX])
fi
fi


if test "$ENABLE_LUATEX" = "true" ; then
    SRC=main
	CLASS=word
	TEXDEPS=word.cls
	LUAFLAG=-pdf
fi
if test "$ENABLE_XETEX" = "true" ;then
    SRC=main
	CLASS=word
	TEXDEPS=word.cls
	XEFLAG=-xelatex
fi

if test "$ENABLE_PTEX" = "true" ; then
    SRC=main
	CLASS=word
	TEXDEPS=word.cls
fi


if test "$ENABLE_LUATEX" = "false" && test "$ENABLE_XETEX" = "false"; then
    SRC=main
    CLASS=word
    TEXDEPS=word.cls
fi

STYDEPS="word-pdf.sty wordlogo.sty"

AC_SUBST(SRC)
AC_SUBST(CLASS)
AC_SUBST(TEXDEPS)
AC_SUBST(STYDEPS)
AC_SUBST(LUAFLAG)
AC_SUBST(XEFLAG)

AC_CONFIG_FILES([Makefile])
AC_OUTPUT
