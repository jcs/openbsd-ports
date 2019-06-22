# $OpenBSD: Makefile,v 1.23 2010/11/22 08:37:04 espie Exp $

COMMENT=	minimal wm based on GNU screen

GH_ACCOUNT =	jcs
GH_PROJECT =	ratpoison
GH_COMMIT =	36e957e8c74e7a1b8aa132b8197e25097f662d5d
DISTNAME =	${GH_PROJECT}-${GH_ACCOUNT}-20180816
CATEGORIES =	x11

MAINTAINER=	jcs@openbsd.org

# GPL
PERMIT_PACKAGE_CDROM=	Yes
PERMIT_PACKAGE_FTP=	Yes

WANTLIB=	X11 Xau Xdmcp Xext Xft Xinerama Xrender Xtst c expat \
		fontconfig freetype z xcb Xrandr

BUILD_DEPENDS=	${MODGNU_AUTOCONF_DEPENDS} \
		${MODGNU_AUTOMAKE_DEPENDS}

FLAVORS=	xft
FLAVOR?=	xft

CONFIGURE_STYLE= gnu
AUTOCONF_VERSION= 2.69
AUTOMAKE_VERSION= 1.15
CONFIGURE_ARGS+= --with-xterm=${X11BASE}/bin/xterm

.if ${FLAVOR:Mxft}
CONFIGURE_ARGS+= --with-xft
WANTLIB+=	Xft
.else
CONFIGURE_ARGS+= --without-xft
.endif

pre-configure:
	@cd ${WRKSRC} && \
	AUTOCONF_VERSION=${AUTOCONF_VERSION} \
	AUTOMAKE_VERSION=${AUTOMAKE_VERSION} \
	autoreconf -i

.include <bsd.port.mk>
