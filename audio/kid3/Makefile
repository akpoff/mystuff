# $OpenBSD$

COMMENT =	application to edit the ID3v1 and ID3v2 tags

DISTNAME =	kid3-3.4.1
CATEGORIES =	audio x11

SHARED_LIBS +=  kid3-core            0.0 # 3.4
SHARED_LIBS +=  kid3-gui             0.0 # 3.4

MASTER_SITES=	${MASTER_SITE_SOURCEFORGE:=kid3/}

HOMEPAGE =	http://kid3.sourceforge.net/

MAINTAINER =	Aaron Poffenberger <akp@hypernote.com>

# GPLv2
PERMIT_PACKAGE_CDROM =	Yes

WANTLIB +=	c m pthread stdc++ z
WANTLIB +=	FLAC FLAC++ chromaprint id3 ogg tag vorbis vorbisfile
WANTLIB +=	glib-2.0 gmodule-2.0 gobject-2.0 gstreamer-0.10 gthread-2.0
WANTLIB +=	intl phonon readline termcap xml2
WANTLIB += 	lib/qt4/QtCore lib/qt4/QtGui lib/qt4/QtNetwork
WANTLIB += 	lib/qt4/QtXml lib/qt4/QtDBus lib/qt4/QtDeclarative

MODULES +=	devel/cmake x11/qt4

BUILD_DEPENDS =	textproc/docbook-xsl
RUN_DEPENDS =	x11/gtk+3,-guic \
		devel/desktop-file-utils \
		multimedia/gstreamer-0.10/plugins-good
LIB_DEPENDS =	audio/chromaprint \
		audio/flac \
		audio/libvorbis \
		audio/taglib \
		audio/id3lib \
		multimedia/gstreamer-0.10/core

# set to use gstreamer-0.10 and disable
# phonon to avoid known issue with gstreamer1
# https://sourceforge.net/p/kid3/bugs/77/
CONFIGURE_ARGS +=	-D"WITH_APPS=Qt;CLI" \
			-DCMAKE_BUILD_TYPE=Release \
			-DWITH_DOCBOOKDIR=${LOCALBASE}/share/xsl/docbook \
			-DWITH_GSTREAMER_VERSION=0.10 \
			-DWITH_MANDIR=man \
			-DWITH_NO_MANCOMPRESS=ON \
			-WITH_PHONON=OFF \
			-DWITH_QT4=ON

WRKBUILD =		${WRKSRC}

.include <bsd.port.mk>
