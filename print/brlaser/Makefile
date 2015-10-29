# $OpenBSD: Makefile,v 1.18 2013/08/09 16:53:45 ajacoutot Exp $

COMMENT=	CUPS printer driver for some Brother laser printers

V=		3
DISTNAME=	v${V}
DIST_SUBDIR=	brlaser
PKGNAME=	${DIST_SUBDIR}-${V}

CATEGORIES=	print
HOMEPAGE=	https://github.com/pdewacht/brlaser

MAINTAINER=	joshua stein <jcs@openbsd.org>

MASTER_SITES=	${HOMEPAGE}/archive/

# GPLv2
PERMIT_PACKAGE_CDROM= Yes

WANTLIB+=	c pthread cups cupsimage
LIB_DEPENDS=	print/cups,-libs

MODULES+=	converters/libiconv \
		gcc4
MODGCC4_ARCHS=	*
MODGCC4_LANGS=	c++

CONFIGURE_STYLE= gnu
AUTOCONF_VERSION=2.69
AUTOMAKE_VERSION=1.15

WRKDIST=	${WRKDIR}/${PKGNAME}

post-patch:
	@cd ${WRKSRC} && env AUTOCONF_VERSION=${AUTOCONF_VERSION} \
		AUTOMAKE_VERSION=${AUTOMAKE_VERSION} NOCONFIGURE=1 ./autogen.sh

.include <bsd.port.mk>
