# $OpenBSD$

COMMENT=	BBS terminal program

DISTNAME=	syncterm-1.0
HOMEPAGE=	http://syncterm.bbsdev.net/

EXTRACT_SUFX=	.tgz
MASTER_SITES=	${MASTER_SITE_SOURCEFORGE:=syncterm/}

# GPLv2
PERMIT_PACKAGE_CDROM=	Yes

WANTLIB +=	c curses m ossaudio pthread util

CATEGORIES=	comms net

USE_GMAKE=	Yes
# SDL gets dlopen'd at runtime
RUN_DEPENDS=	devel/sdl

MAKE_FILE=	GNUmakefile
MAKE_FLAGS=	WITHOUT_CRYPTLIB=1 \
		USE_SDL=1 \
		SDL_CONFIG=${LOCALBASE}/bin/sdl-config \
		QUIET=

FAKE_FLAGS=	PREFIX=${PREFIX}

WRKSRC=		${WRKDIST}/src/syncterm

.include <bsd.port.mk>
