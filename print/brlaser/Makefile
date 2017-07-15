# $OpenBSD: Makefile,v 1.18 2013/08/09 16:53:45 ajacoutot Exp $

COMMENT=	CUPS printer driver for some Brother laser printers

V=		3
DISTNAME=	brlaser-${V}

CATEGORIES=	print
HOMEPAGE=	https://github.com/pdewacht/brlaser

MAINTAINER=	joshua stein <jcs@openbsd.org>

MASTER_SITES=	https://github.com/pdewacht/brlaser/releases/download/v$V/

# GPLv2
PERMIT_PACKAGE_CDROM= Yes

WANTLIB+=	c pthread cups cupsimage
LIB_DEPENDS=	print/cups,-libs

MODULES+=	gcc4
MODGCC4_ARCHS=	*
MODGCC4_LANGS=	c++

BUILD_DEPENDS =	${MODGNU_AUTOCONF_DEPENDS} \
		${MODGNU_AUTOMAKE_DEPENDS}

CONFIGURE_STYLE= gnu
AUTOCONF_VERSION=2.69
AUTOMAKE_VERSION=1.15

.include <bsd.port.mk>
