# $OpenBSD$

COMMENT=	BBS terminal program

PKGNAME=	syncterm-1.1
DISTNAME=	${PKGNAME}-src
HOMEPAGE=	http://syncterm.bbsdev.net/

EXTRACT_SUFX=	.tgz
MASTER_SITES=	${MASTER_SITE_SOURCEFORGE:=syncterm/}

# GPLv2
PERMIT_PACKAGE=	Yes

WANTLIB +=	c curses m ossaudio pthread util

CATEGORIES=	comms net

USE_GMAKE=	Yes
BUILD_DEPENDS=	devel/sdl2
# SDL gets dlopen'd at runtime
RUN_DEPENDS=	${LIB_DEPENDS}

MAKE_FILE=	GNUmakefile
MAKE_FLAGS=	RELEASE=1 \
		WITHOUT_CRYPTLIB=1 \
		USE_SDL=1 \
		SDL_CONFIG=${LOCALBASE}/bin/sdl2-config \
		QUIET=
CFLAGS+=	-DN_CURSES_LIB -D_XOPEN_SOURCE_EXTENDED=1

FAKE_FLAGS=	PREFIX=${PREFIX}

WRKDIST=	${WRKDIR}/${PKGNAME}/src/syncterm

post-install:
	gzip -d ${PREFIX}/man/man1/syncterm.1.gz

.include <bsd.port.mk>
