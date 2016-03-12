# $OpenBSD: Makefile.template,v 1.73 2016/01/11 09:17:22 sthen Exp $

COMMENT=	software for manipulation of Biblical texts.

DISTNAME=	sword-1.7.5
PKGNAME=	sword-1.7.5a1

SHARED_LIBS =	sword 1.7

CATEGORIES=	misc

HOMEPAGE=	http://www.crosswire.org/sword/develop/index.jsp

MAINTAINER=	Aaron Poffenberger <akp@hypernote.com>

# GPLv2
PERMIT_PACKAGE_CDROM=	Yes

MASTER_SITES=		http://www.crosswire.org/ftpmirror/pub/sword/source/v1.7/

MODULES=	devel/cmake

CONFIGURE_STYLE=	cmake
NO_TEST =		Yes

.include <bsd.port.mk>
