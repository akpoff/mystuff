# $OpenBSD: Makefile,v 1.49 2016/01/20 16:27:42 kili Exp $

COMMENT-main =		document converter written in Haskell
COMMENT-lib =		document converter library written in Haskell

DISTNAME =		pandoc-1.17.1
MODGHC_CABAL_PKGS =	pandoc-1.17.1 \
			HTTP-4000.3.3 \
			JuicyPixels-3.2.7.1 \
			asn1-encoding-0.9.4 \
			asn1-parse-0.9.4 \
			asn1-types-0.3.2 \
			async-2.1.0 \
			blaze-builder-0.4.0.2 \
			blaze-html-0.8.1.1 \
			blaze-markup-0.7.0.3 \
			byteable-0.1.1 \
			case-insensitive-1.2.0.6 \
			cereal-0.5.2.0 \
			cmark-0.5.2.1 \
			conduit-1.2.6.6 \
			connection-0.2.5 \
			cookie-0.4.2 \
			cryptonite-0.17 \
			data-default-class-0.1.1 \
			enclosed-exceptions-1.0.1.1 \
			exceptions-0.8.2.1 \
			fail-4.9.0.0 \
			filemanip-0.3.6.3 \
			haddock-library-1.4.2 \
			highlighting-kate-0.6.2 \
			hourglass-0.2.10 \
			hslua-0.4.1 \
			http-client-0.4.28 \
			http-client-tls-0.2.4 \
			http-types-0.9.1 \
			lifted-base-0.2.3.6 \
			memory-0.13 \
			mime-types-0.1.0.7 \
			mmorph-1.0.6 \
			monad-control-1.0.1.0 \
			pem-0.2.2 \
			regex-base-0.93.2 \
			regex-pcre-builtin-0.94.4.8.8.35 \
			resourcet-1.1.7.4 \
			semigroups-0.18.1 \
			socks-0.5.5 \
			stm-2.4.4.1 \
			streaming-commons-0.1.15.5 \
			tagged-0.8.4 \
			tagsoup-0.13.10 \
			temporary-1.2.0.4 \
			texmath-0.8.6.3 \
			tls-1.3.8 \
			transformers-base-0.4.4 \
			transformers-compat-0.5.1.4 \
			unix-compat-0.4.2.0 \
			x509-1.6.3 \
			x509-store-1.6.1 \
			x509-system-1.6.3 \
			x509-validation-1.6.3 \
			xml-1.3.14 \
			yaml-0.8.17.2

PKGNAME-main =		${DISTNAME}
PKGNAME-lib =		${DISTNAME:S,-,-lib-,}
REVISION-lib =		1
CATEGORIES =		converters
HOMEPAGE =		http://pandoc.org/
MAINTAINER =		Aaron Poffenberger <akp@hypernote.com>

MASTER_SITES0 =		https://hackage.haskell.org/package/
.for _pkg in ${MODGHC_CABAL_PKGS}
DISTFILES +=		${_pkg}/${_pkg}.tar.gz:0
.endfor

EXTRACT_ONLY =		${DISTNAME}/${DISTNAME}.tar.gz

MULTI_PACKAGES =		-main -lib

# GPL 2
PERMIT_PACKAGE_CDROM =	Yes

WANTLIB-main +=		${WANTLIB} c m pthread util z
WANTLIB-lib =

MODULES =		lang/ghc converters/libiconv
MODGHC_BUILD =		cabal sandbox hackage haddock register nort

MODGHC_PACKAGE_KEY =	A55c2e4ucsN2M0NPtFuf5e

# Required because of the nort tag in MODGHC_BUILD
SUBST_VARS +=		MODGHC_PACKAGE_KEY

BUILD_DEPENDS-lib =	${RUN_DEPENDS-lib}
RUN_DEPENDS-lib =	devel/hs-aeson \
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
LIB_DEPENDS-main =	${LIB_DEPENDS}

# MODGHC_BUILD contains 'nort', an explicit dependency is needed for
# the -lib subpackage (plus the tweaks to MODGHC_SETUP_CONF_ARGS below).
RUN_DEPENDS-lib +=		lang/ghc=${MODGHC_VER}

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
