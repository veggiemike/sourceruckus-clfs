SUBDIRS=
#SUBDIRS+=packages
SUBDIRS+=utils

EXTRA_DIST=
EXTRA_DIST+=MIRRORS
EXTRA_DIST+=get_sources
EXTRA_DIST+=get_sources.sha256sums
EXTRA_DIST+=init_submodules


.PHONY: download
download:
	./init_submodules @INIT_SUBMOD_ARGS@
	./get_sources @GET_SOURCES_ARGS@

clean-local:
	rm -rf $(builddir)/.build
	rm -f $(builddir)/.previous_flags
