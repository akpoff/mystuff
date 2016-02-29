# $OpenBSD: Makefile.template,v 1.71 2014/07/10 12:33:17 sthen Exp $

COMMENT=	USRP Hardware Driver

DISTNAME=	release_003_009_002
REVISION=   0

DISTNAME=	uhd-${GH_TAGNAME}
PKGNAME=	uhd-${GH_TAGNAME:S/release_//}

GH_ACCOUNT=	EttusResearch
GH_PROJECT=	uhd
GH_TAGNAME=	release_003_009_002

SHARED_LIBS +=		uhd  0.0

CATEGORIES=	comms

HOMEPAGE=	http://files.ettus.com/manual/

MAINTAINER=	Aaron Poffenberger <akp@hypernote.com>

# GPLv3
PERMIT_PACKAGE_CDROM=	Yes

# Dependencies
WANTLIB += c curses form m pthread stdc++ usb-1.0
WANTLIB += boost_date_time-mt boost_filesystem-mt
WANTLIB += boost_program_options-mt
WANTLIB += boost_regex-mt     boost_serialization-mt
WANTLIB += boost_system-mt    boost_thread-mt
WANTLIB += boost_unit_test_framework-mt

MODULES += devel/cmake lang/python
BUILD_DEPENDS=	devel/doxygen
RUN_DEPENDS=	www/py-mako
LIB_DEPENDS=	devel/libusb1 devel/boost>=1.46

CONFIGURE_STYLE = cmake

# Only build with clang at the moment
# See TODO
CONFIGURE_ARGS += \
	-DCMAKE_C_COMPILER=/usr/local/bin/clang \
	-DCMAKE_CXX_COMPILER=/usr/local/bin/clang++ \
	-DPYTHON_EXECUTABLE=/usr/local/bin/python2.7

WRKSRC= ${WRKDIST}/host

.include <bsd.port.mk>
