
## 在Ubuntu下编译FTK

- ./autogen.sh
- ./configure --with-backend=linux-x11:320x480 --enable-opengles=no
- make
- sudo make install

## 常见问题

* configure.ac:14: warning: macro 'AM_GLIB_GNU_GETTEXT' not found in library
解决：apt-get install libglib2.0-dev

* ftk_image_jpeg_decoder.c:35:21: error: jpeglib.h: No such file or directory
解决：apt-get install libjpeg62-dev

* ftk_image_png_decoder.c:36:17: error: png.h: No such file or directory
解决：apt-get install libpng12-dev

* ../libtool: line 984: g++: command not found
解决：apt-get install g++

* ./backend/x11-emu/ftk_display_x11.c:33:22: error: X11/Xlib.h: No such file or directory
解决：apt-get install libx11-dev

* gcc: /home/nicer/ftk-0.6.2/src/.libs/libftk.so: No such file or directory
解决：./configure --with-backend=linux-x11:320x480 --enable-shared

* /usr/bin/ld: cannot find -lXext
解决：apt-get install libxext-dev

* ./autogen.sh: 4: aclocal: not found
解决：sudo apt-get install automake

* ./autogen.sh: 7: gtkdocize: not found
解决：apt-get install gtk-doc-tools

* i386-linux-gnu/libm.so: error adding symbols: DSO missing from command line collect2: error: ld returned 1 exit status
解决：./configure LIBS="-lm"

* make[1]: *** [install-data-yes] Error 127
解决：把po/Makefile.in.in里
    $(SHELL) $(top_srcdir)/$(MKINSTALLDIRS) $(DESTDIR)$(datadir);
改成
    $(SHELL) $(top_srcdir)/install-sh -d $(DESTDIR)$(datadir);
