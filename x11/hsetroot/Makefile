# $OpenBSD$

COMMENT=	wallpaper setting utility

DISTNAME=	hsetroot-20190111
GH_COMMIT=	1c31cfc884eccfa3e90e99c8cd80d285cd7a62ea
GH_ACCOUNT=	himdel
GH_PROJECT=	hsetroot

CATEGORIES=	x11

# GPLv2
PERMIT_PACKAGE_CDROM=Yes

WANTLIB=	Imlib2 c X11

LIB_DEPENDS=	graphics/imlib2

MAKE_ENV=	CFLAGS=-I${X11BASE}/include \
		LDFLAGS=-L${X11BASE}/lib
NO_TEST= 	Yes
USE_GMAKE=	Yes

ALL_TARGET=	hsetroot

do-install:
	${INSTALL_PROGRAM} ${WRKDIST}/hsetroot ${PREFIX}/bin/

.include <bsd.port.mk>
