> Trouver tous les fichiers avec une définition de _main_
``` bash
gnuplot-5.0.7/src 
[I] ➜ grep -E -r '^main.*)$' .
./bf_test.c:main(void)
./plot.c:main(int argc, char **argv)
./strftime.c:main()
./gplt_x11.c:main(int argc, char *argv[])
./gplt_x11.c:mainloop()
./gplt_x11.c:mainloop()
./gplt_x11.c:mainloop()
./win/winmain.c:main(int argc, char **argv)
./win/pgnuplot.c:main (int argc, char *argv[])
```

> Trouver tous les fichiers qui incluent alloc.h

```bash 
gnuplot-5.0.7/src 
[I] ➜ grep -E -r '*[[:space:]]alloc\.h' . 
./alloc.h: * $Id: alloc.h,v 1.14 2014/08/18 04:43:29 sfeam Exp $
./alloc.h:/* GNUPLOT - alloc.h */
./qtterminal/.deps/qt_term.Po: getcolor.h command.h util.h alloc.h parse.h axis.h gadgets.h term_api.h \
./Makefile.am:gnuplot_SOURCES = alloc.c alloc.h axis.c axis.h breaders.c breaders.h bitmap.h \
./Makefile.in:am__gnuplot_SOURCES_DIST = alloc.c alloc.h axis.c axis.h breaders.c \
./Makefile.in:gnuplot_SOURCES = alloc.c alloc.h axis.c axis.h breaders.c breaders.h 
(...)
```

> Trouver tous les fichiers datant de moins de 15 jours
> 
<!--stackedit_data:
eyJoaXN0b3J5IjpbNDQzMDE4NzQ3LC03MjY2ODg5MTksNzYxMj
Q3Njc2XX0=
-->