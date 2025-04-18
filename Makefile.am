## Makefile.am
##
## Top level Makefile.am
##
##   (C) Copyright 2025 Fred Gleason <fredg@paravelsystems.com>
##
##   This program is free software; you can redistribute it and/or modify
##   it under the terms of the GNU General Public License version 2 as
##   published by the Free Software Foundation.
##
##   This program is distributed in the hope that it will be useful,
##   but WITHOUT ANY WARRANTY; without even the implied warranty of
##   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
##   GNU General Public License for more details.
##
##   You should have received a copy of the GNU General Public
##   License along with this program; if not, write to the Free Software
##   Foundation, Inc., 675 Mass Ave, Cambridge, MA 02139, USA.
##
## Use automake to process this into a Makefile.in

SUBDIRS = debian

all:
	./build_tarball.sh

maintainer-clean-local:
	./clean_build.sh

deb:	all
	./build_debs.sh

rpm:	all
	cp aws-sdk-cpp-$(VERSION).tar.gz $(HOME)/rpmbuild/SOURCES/
	$(RPMBUILD) -ba --target $(ARCH)-$(VENDOR)-linux aws-sdk-cpp.spec
	mv $(HOME)/rpmbuild/RPMS/$(ARCH)/aws-sdk-cpp-*.rpm $(top_srcdir)/
	mv $(HOME)/rpmbuild/SRPMS/aws-sdk-cpp-*.src.rpm $(top_srcdir)/
	rm $(HOME)/rpmbuild/SOURCES/aws-sdk-cpp-$(VERSION).tar.gz
	rm -rf $(HOME)/rpmbuild/BUILD/aws-sdk-cpp-$(VERSION)

EXTRA_DIST = autogen.sh\
             build_tarball.sh.in\
             build_debs.in\
             clean_build.sh\
             CODINGSTYLE\
             get_distro.pl\
             get_target.sh\
             aws-sdk-cpp.spec.in

CLEANFILES = *~\
             *.buildinfo\
             *.changes\
             *.ddeb\
             *.deb\
             *.dsc\
             *.mo\
             *.rpm\
             *.tar.gz\
             *.tar.xz\
             *.tgz\
             *.zip

DISTCLEANFILES = aws-sdk-cpp.spec\
                 build_debs.sh\
                 build_tarball.sh\
                 config.guess\
                 config.sub\
                 ltmain.sh

MAINTAINERCLEANFILES = *~\
                       *.tar.gz\
                       API_VERSION\
                       aclocal.m4\
                       compile\
                       config.guess\
                       config.status\
                       config.sub\
                       configure\
                       depcomp\
                       install-sh\
                       libtool\
                       ltmain.sh\
                       Makefile.in\
                       missing\
                       mkinstalldirs
