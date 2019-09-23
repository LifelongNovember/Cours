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
gnuplot-5.0.7 took 8s 
[I] ✘130 ➜ ls ~ -alR | grep "oct\. [[:space:]]*201[0-9]"
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTYwOTk3NDQ5Myw2NzMzMzY1ODYsMTkxOT
I3Njg2LDQ0MzAxODc0NywtNzI2Njg4OTE5LDc2MTI0NzY3Nl19

-->