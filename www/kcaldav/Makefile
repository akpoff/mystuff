# $OpenBSD$

COMMENT-main =		a simple, safe, and minimal CalDAV server
COMMENT-cgi = 		cgi components for kcaldav

V=			0.1.4
DISTNAME =		kcaldav-${V}
PKGNAME=		kcaldav-${V}
PKGNAME-main =		kcaldav-main-${V}
PKGNAME-cgi =		kcaldav-cgi-${V}
CATEGORIES =		www

HOMEPAGE =		http://kristaps.bsd.lv/kcaldav/
MAINTAINER =		Aaron Poffenberger <akp@hypernote.com>

# ISC
PERMIT_PACKAGE_CDROM =	Yes

# "make port-lib-depends-check" can help
WANTLIB +=		c expat m sqlite3

MULTI_PACKAGES=		-main -cgi

MASTER_SITES =		http://kristaps.bsd.lv/kcaldav/snapshots/
DISTFILES =		kcaldav.tgz

BUILD_DEPENDS =		www/kcgi
RUN_DEPENDS-cgi =	www/kcaldav

PREFIX-cgi =		${VARBASE}/www
FAKE_FLAGS =		PREFIX=${WRKDIR}/fake-amd64/usr/local WWWPREFIX=${WRKDIR}/fake-amd64/var/www

# no doc on how to run tests
NO_TEST =		Yes

ALL_TARGET =		all libkcaldav.a
INSTALL_TARGET =	install installcgi

post-install:
	@export ${FAKE_FLAGS}; \
		mkdir -p $$WWWPREFIX/tmp; \
		chmod a+w $$WWWPREFIX/tmp;

.include <bsd.port.mk>
