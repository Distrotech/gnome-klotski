bin_PROGRAMS = gnome-klotski

BUILT_SOURCES = klotski-resources.c

gnome_klotski_SOURCES = \
	config.vapi \
	gnome-klotski.vala \
	history.vala \
	puzzle.vala \
	puzzle-view.vala \
	score-dialog.vala \
	$(BUILT_SOURCES)

gnome_klotski_CFLAGS = \
	-DVERSION=\"$(VERSION)\" \
	-DGETTEXT_PACKAGE=\"$(GETTEXT_PACKAGE)\" \
	-DDATA_DIRECTORY=\"$(datadir)/gnome-klotski\" \
	-DLOCALEDIR=\"$(datadir)/locale\" \
	-w \
	$(GNOME_KLOTSKI_CFLAGS)

gnome_klotski_VALAFLAGS = \
	--pkg posix \
	--pkg gtk+-3.0 \
	--pkg librsvg-2.0 \
	--gresources $(builddir)/klotski.gresource.xml \
	--target-glib $(GLIB_REQUIRED)

gnome_klotski_LDADD = \
	$(GNOME_KLOTSKI_LIBS)

klotski-resources.c: $(shell $(GLIB_COMPILE_RESOURCES) --generate-dependencies klotski.gresource.xml)
	$(AM_V_GEN) $(GLIB_COMPILE_RESOURCES) --target=$@ --sourcedir=$(srcdir) --generate-source klotski.gresource.xml

CLEANFILES = \
	$(patsubst %.vala,%.c,$(filter %.vala, $(SOURCES))) \
	*_vala.stamp

DISTCLEANFILES = \
	Makefile.in

MAINTAINERCLEANFILES = klotski-resources.c

EXTRA_DIST = klotski.gresource.xml

-include $(top_srcdir)/git.mk
