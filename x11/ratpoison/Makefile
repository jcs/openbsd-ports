# $OpenBSD: Makefile,v 1.23 2010/11/22 08:37:04 espie Exp $

COMMENT=	minimal wm based on GNU screen

GH_ACCOUNT =	jcs
GH_PROJECT =	ratpoison
GH_COMMIT =	2b2b591fcb811dd3c4e01003276cd396088774d1
DISTNAME =	${GH_PROJECT}-${GH_ACCOUNT}-20110616
CATEGORIES =	x11

MAINTAINER=	jcs@openbsd.org

# GPL
PERMIT_PACKAGE_CDROM=	Yes
PERMIT_PACKAGE_FTP=	Yes

WANTLIB=		X11 Xau Xdmcp Xext Xft Xinerama Xrender Xtst c expat \
			fontconfig freetype z pthread-stubs xcb

USE_GROFF =		Yes

CONFIGURE_STYLE=	gnu

CONFIGURE_ARGS+=	--with-xterm=${X11BASE}/bin/xterm

.include <bsd.port.mk>
