# $OpenBSD: Makefile,v 1.23 2010/11/22 08:37:04 espie Exp $

COMMENT=	minimal wm based on GNU screen

GH_ACCOUNT =	jcs
GH_PROJECT =	ratpoison
GH_COMMIT =	4a2b462cbfe64b31abad3b9363b233f54a493432
DISTNAME =	${GH_PROJECT}-${GH_ACCOUNT}-20161223
CATEGORIES =	x11

MAINTAINER=	jcs@openbsd.org

# GPL
PERMIT_PACKAGE_CDROM=	Yes
PERMIT_PACKAGE_FTP=	Yes

WANTLIB=		X11 Xau Xdmcp Xext Xft Xinerama Xrender Xtst c expat \
			fontconfig freetype z pthread-stubs xcb

BUILD_DEPENDS=	${MODGNU_AUTOCONF_DEPENDS} \
		${MODGNU_AUTOMAKE_DEPENDS}

CONFIGURE_STYLE=	gnu
AUTOCONF_VERSION=	2.69
AUTOMAKE_VERSION=	1.15
CONFIGURE_ARGS+=	--with-xterm=${X11BASE}/bin/xterm

pre-configure:
	@cd ${WRKSRC} && \
		AUTOCONF_VERSION=${AUTOCONF_VERSION} \
		AUTOMAKE_VERSION=${AUTOMAKE_VERSION} \
		autoreconf -i

.include <bsd.port.mk>
