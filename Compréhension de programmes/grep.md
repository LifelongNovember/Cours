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
```bash
gnuplot-5.0.7 
[I] ➜ find . -type f ! -ctime 15
./Makefile.maint
./share/colors_default.gp
./share/colors_podo.gp
./share/colors_mono.gp
./share/Makefile.am
./share/gnuplotrc
(...)
```
> Trouver tous les fichiers datant de moins de 15 jours et contenant EXTERN
> 
```bash
gnuplot-5.0.7 
[I] ➜ find . ! -ctime 15 -type f | grep -r "EXTERN"
config.status:D["HAVE_EXTERNAL_FUNCTIONS"]=" 1"
config.status:D["EXTERNAL_X11_WINDOW"]=" 1"
config.hin:#undef EXTERNAL_X11_WINDOW
config.hin:#undef EXTERN_ERRNO
config.hin:#undef HAVE_EXTERNAL_FUNCTIONS
demo/plugin/plugin.dem:if (!strstrt(GPVAL_COMPILE_OPTIONS,"+EXTERNAL_FUNCTIONS")) {
config/config.mgw:/* #undef EXTERNAL_X11_WINDOW */
config/config.mgw:/* #undef EXTERN_ERRNO */
config/config.mgw:#define HAVE_EXTERNAL_FUNCTIONS 1
config/config.nt:/* #undef EXTERNAL_X11_WINDOW */
(...)
```

> Trouver tous les fichiers executables

```bash
gnuplot-5.0.7 
[I] ✘1 ➜ find . -type f -executable 
./config.status
./demo/html/webify_svg.pl
./demo/html/webify.pl
./demo/html/webify_canvas.pl
./demo/plugin/demo_plugin.so
./config/MacOSX/PkgResources/InstallationCheck
./config/MacOSX/PkgResources/postinstall
./config/djconfig.sh
(...)
```
> Trouver tous les fichiers avec une date de modification en octobre
```bash
gnuplot-5.0.7
[I] ➜ find . -exec ls -al '{}' \; | grep "oct\. [[:space:]]*201[0-9]"
-rw-r--r--  1 novembre novembre   4990 24 oct.   2013 TODO
-rw-r--r--  1 novembre novembre  1794  5 oct.   2015 imageNaN.dem
-rw-r--r--  1 novembre novembre  5578 31 oct.   2010 pm3dcolors.dem
-rw-r--r--  1 novembre novembre 11630  4 oct.   2012 pm3d.dem
-rw-r--r--  1 novembre novembre  3526 30 oct.   2012 rgb_variable.dem
-rw-r--r--  1 novembre novembre  1331 10 oct.   2012 smooth.dem
-rw-r--r--  1 novembre novembre  1523 24 oct.   2015 timedat.dem
-rw-r--r--  1 novembre novembre  3198 10 oct.   2012 varcolor.dem
-rw-r--r-- 1 novembre novembre 3198 10 oct.   2012 ./demo/varcolor.dem
(...)
```
> -   Trouver tous les fichier avec moins de 50 octets

```bash
gnuplot-5.0.7 
[I] ➜ find . -size -50c -type f       
./demo/line.fnc
./demo/histopt.dat
./config/watcom/config.h
./stamp-h
./docs/.deps/doc2wxhtml.Po
./VERSION
./PATCHLEVEL
(...)
```
> Trouver tous les fichier avec plus de 500000 octets
``` bash
gnuplot-5.0.7 
[I] ➜ find . -size +500000c -type f
./gnuplot/5.0/gnuplot.gih
./bin/gnuplot
./docs/gnuplot.pdf
./docs/gnuplot.doc
./docs/gnuplot-ja.doc
./docs/gnuplot.gih
./configure
./src/qtterminal/QtGnuplotItems.o
./src/qtterminal/QtGnuplotWindow.o
(...)
```
> Trouver tous les fichiers contenant 1 seule ligne
``` bash
gnuplot-5.0.7 
[I] ➜ find . -type f -exec wc -L '{}' \; | grep "^1[[:space:]]"
1 ./PATCHLEVEL
```

>Afficher le nb de lignes de tous makefile de l'archive

``` bash
gnuplot-5.0.7 
[I] ➜ find . -name "*[mM]akefile" -exec wc -L '{}' \;
576 ./share/LaTeX/Makefile
576 ./share/Makefile
1205 ./demo/html/Makefile
576 ./demo/plugin/Makefile
576 ./demo/Makefile
159 ./config/mingw/Makefile
214 ./config/msvc/Makefile
118 ./config/cygwin/Makefile
119 ./config/watcom/Makefile
576 ./config/Makefile
79 ./GNUmakefile

```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE5MzYyNzA2NDIsMzcyNjM4OTMxLDI5NT
MwNzI4LDE2MDk5NzQ0OTMsNjczMzM2NTg2LDE5MTkyNzY4Niw0
NDMwMTg3NDcsLTcyNjY4ODkxOSw3NjEyNDc2NzZdfQ==
-->