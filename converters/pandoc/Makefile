# $OpenBSD: Makefile,v 1.49 2016/01/20 16:27:42 kili Exp $

COMMENT =		nearly universal document converter

DISTNAME =		pandoc-1.17.1
PKGNAME =		${DISTNAME}
CATEGORIES =		converters
HOMEPAGE =		http://pandoc.org/
MAINTAINER =		Aaron Poffenberger <akp@hypernote.com>

# GPL 2
PERMIT_PACKAGE_CDROM =	Yes

WANTLIB +=		c m pthread util z

MODULES =		lang/ghc converters/libiconv
MODGHC_BUILD =		cabal sandbox hackage haddock nort

# Required because of the nort tag in MODGHC_BUILD
SUBST_VARS +=		MODGHC_PACKAGE_KEY

BUILD_DEPENDS =		devel/hs-aeson \
			devel/hs-base64-bytestring \
			devel/hs-data-default \
			devel/hs-extensible-exceptions \
			devel/hs-mtl \
			devel/hs-network \
			devel/hs-network-uri \
			devel/hs-old-locale \
			devel/hs-old-time \
			devel/hs-parsec \
			devel/hs-random \
			devel/hs-syb \
			devel/hs-unordered-containers \
			devel/hs-vector

post-install:
	@${INSTALL_MAN} ${WRKSRC}/man/pandoc.1 ${PREFIX}/man/man1

# Needs to be built with different configuration.
NO_TEST =	Yes

.include <bsd.port.mk>

# Override the 'nort' settings from ghc.port.mk, to get the correct
# flags and directories for the -lib subpackage.
MODGHC_SETUP_CONF_ARGS +=	--enable-library-profiling
MODGHC_SETUP_CONF_ARGS +=	--docdir=\$$datadir/doc/hs-\$$pkgid
MODGHC_SETUP_CONF_ARGS +=	--libsubdir=ghc/\$$pkgid
