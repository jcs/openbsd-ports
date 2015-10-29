# $OpenBSD: Makefile,v 1.23 2010/11/22 08:37:04 espie Exp $

COMMENT=	minimal wm based on GNU screen

GH_ACCOUNT =	jcs
GH_PROJECT =	ratpoison
GH_COMMIT =	7018e1d15cd4de7f2fbca3fa7d82f0389015d7a9
DISTNAME =	${GH_PROJECT}-${GH_ACCOUNT}-20151029
CATEGORIES =	x11

MAINTAINER=	jcs@openbsd.org

# GPL
PERMIT_PACKAGE_CDROM=	Yes
PERMIT_PACKAGE_FTP=	Yes

WANTLIB=		X11 Xau Xdmcp Xext Xft Xinerama Xrender Xtst c expat \
			fontconfig freetype z pthread-stubs xcb

CONFIGURE_STYLE=	gnu

CONFIGURE_ARGS+=	--with-xterm=${X11BASE}/bin/xterm

.include <bsd.port.mk>
