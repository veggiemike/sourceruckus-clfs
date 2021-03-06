SUBDIRS =

# Before we get started w/ CLFS stuff, lets build a busybox package that
# slurps up the cross-compiled busybox files we built during
# bootstrap-stage1.
#
SUBDIRS += busybox

# BEGIN CLFS Chapter 10 - Installing Basic System Software
#
# Deviations for CLFS will be noted appropriately.
#
SUBDIRS += man-pages

# NOTE: This package has been pulled out of the CLFS glibc chapter where it was
#       oddly hidden...
#
# FIXME: Building requires zic, which is a part of glibc, so we might have
#        to wait to build this package until after we've installed
#        glibc... but for now I'm trying it using the cross-compiled zic
#        in /tools.
#
#        Seems to work fine...
#
SUBDIRS += tzdata

# NOTE: glibc assumes ownership of all headers in /usr/include under the
#       assumption that they're the kernel headers previously installed in
#       bootstrap-stage2.  don't put anything before glibc that installs
#       files in /usr/include
#
# FIXME: double-check that man-pages and tzdata don't install files in
#        /usr/include
#
# NOTE: glibc has a post-install script that correlates w/ CLFS's
#       "Adjusting the Toolchain" step.  This will modify the specs for
#       /tools*/bin/gcc to compile against the newly installed glibc
#       instead of the bootstrap version in /tools*/lib.  Don't attempt to
#       build/install glibc outside the bootstrap environment.  Bad things
#       will happen.
#
SUBDIRS += glibc

FOOSUBDIRS =
FOOSUBDIRS += m4
FOOSUBDIRS += gmp
FOOSUBDIRS += mpfr
FOOSUBDIRS += mpc
FOOSUBDIRS += isl
FOOSUBDIRS += cloog
FOOSUBDIRS += zlib
FOOSUBDIRS += flex
FOOSUBDIRS += bison
FOOSUBDIRS += binutils
FOOSUBDIRS += gcc

# FIXME: these were just for systemd...
#
#SUBDIRS += attr
#SUBDIRS += acl

# bb
#
#SUBDIRS += sed

FOOSUBDIRS += pkg-config # pkg-config-lite?
FOOSUBDIRS += ncurses

# bb
#
#SUBDIRS += shadow
#SUBDIRS += util-linux
#SUBDIRS += procps
#SUBDIRS += e2fsprogs

# FIXME: this was just for systemd
#
#SUBDIRS += libcap

# bb
#
#SUBDIRS += coreutils

FOOSUBDIRS += iana-etc
FOOSUBDIRS += libtool

# FIXME: some equivelent stuff is in bb... but we may need the real deal
#        (unless newer version of bb is way better).
#
#SUBDIRS += iproute2

# bb
#
# FIXME: might want libbzip2...
#
#SUBDIRS += bzip2

# FIXME: what is this...?  GNU Database Manager?  what needs this?  not
#        systemd...  anything?  can we leave this out?
#
#        wasn't this for man-db?
#
#SUBDIRS += gdbm

FOOSUBDIRS += perl
FOOSUBDIRS += readline
FOOSUBDIRS += autoconf
FOOSUBDIRS += automake
FOOSUBDIRS += bash

# FIXME: maybe in newer bb?  doesn't look like it...  but maybe we don't
#        need it?  i seem to recall kernel makefiles needing it at some
#        point...
#
FOOSUBDIRS += bc

# bb
#
#SUBDIRS += diffutils

FOOSUBDIRS += file
FOOSUBDIRS += gawk

# bb
#
#SUBDIRS += findutils

FOOSUBDIRS += gettext

# FIXME: this was just for systemd
#
#SUBDIRS += gperf

# bb
#
#SUBDIRS += grep

FOOSUBDIRS += groff

# bb
#
#SUBDIRS += less
#SUBDIRS += gzip

# FIXME: portions of these are in bb... can we live w/out the missing
#        bits?
#
#SUBDIRS += iputils
#SUBDIRS += kbd

# FIXME: what needed this?  not systemd...  can we remove this?  man-db
#        needs it.
#
#SUBDIRS += libpipeline

# FIXME: portions of these are in bb... can we live w/out the missing
#        bits?
#
#SUBDIRS += man-db

FOOSUBDIRS += make
FOOSUBDIRS += xz

# FIXME: these were just for systemd
#
#SUBDIRS += expat
#SUBDIRS += perl_xml_parser
#SUBDIRS += intltool

# bb
#
#SUBDIRS += kmod
#SUBDIRS += patch
#SUBDIRS += psmisc

# FIXME: CLFS SYSVINIT adds these...  can we leave them out if we use bb
#        init?
#
#SUBDIRS += libestr
#SUBDIRS += libee
#SUBDIRS += rsyslog
#SUBDIRS += sysvinit

# FIXME: reevaluate this... might really be better off with mdev/eudev and
#        bb init
#
#SUBDIRS += systemd
#SUBDIRS += dbus

# bb
#
#SUBDIRS += tar
FOOSUBDIRS += texinfo

# FIXME: CLFS SYSVINIT added this...  gonna try to stick with bb mdev for
#        now.
#
# SUBDIRS += eudev

# bb
#
#SUBDIRS += vim

# NOTE: we use syslinux instead of grub and do magic tricks with ruckusrd.
#
#SUBDIRS += grub
FOOSUBDIRS += ruckusrd
FOOSUBDIRS += syslinux

FOOSUBDIRS += kernel
FOOSUBDIRS += kernel-firmware

# END CLFS Chapter 10 - Installing Basic System Software
#
# Beyond this point, we add what we want and deviate wildly from CLFS.


# FIXME: how should we plumb in the image separation?  maybe fake packages
#        that have a make target to create squashfs images and adjust
#        filesystems instead of building/installing packages?
#
# SUBDIRS += finalize-base
# SUBDIRS += ... more packages ...
# SUBDIRS += finalize-server
#


# FIXME: we're eventually going to want real less (for cached searching),
#        bzip2 (for libbz2), gzip (for libgz), and tar (for
#        incrementals)... but where/when should we add those?  we
#        definately don't need those functions on our base system.  we can
#        probably live w/out them all the way up to a full-fledged
#        development workstation.
