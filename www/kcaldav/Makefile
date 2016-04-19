# $OpenBSD$

COMMENT =		a simple, safe, and minimal CalDAV server

V=			0.1.4
DISTNAME =		kcaldav-${V}
PKGNAME=		kcaldav-${V}
CATEGORIES =		www

HOMEPAGE =		http://kristaps.bsd.lv/kcaldav/
MAINTAINER =		Aaron Poffenberger <akp@hypernote.com>

# ISC
PERMIT_PACKAGE_CDROM =	Yes

# "make port-lib-depends-check" can help
WANTLIB +=		c expat m sqlite3

MASTER_SITES =		http://kristaps.bsd.lv/kcaldav/snapshots/
DISTFILES =		kcaldav.tgz

BUILD_DEPENDS =		www/kcgi
RUN_DEPENDS-cgi =	www/kcaldav

FAKE_FLAGS =		PREFIX=${WRKINST}${TRUEPREFIX} WWWPREFIX=${WRKINST}/var/www

# no doc on how to run tests
NO_TEST =		Yes

ALL_TARGET =		all libkcaldav.a
INSTALL_TARGET =	install installcgi

post-install:
	@export ${FAKE_FLAGS}; \
		mkdir -p $$WWWPREFIX/tmp; \
		chmod a+w $$WWWPREFIX/tmp;

.include <bsd.port.mk>