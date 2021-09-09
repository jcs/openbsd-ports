# $OpenBSD: Makefile,v 1.16 2017/07/18 14:49:38 tb Exp $

COMMENT=		simple X screen locker

GH_ACCOUNT =		jcs
GH_PROJECT =		slock
GH_COMMIT =		336d4ef9757c30d16486d7601f1de74e0eb70cce
DISTNAME =		${GH_PROJECT}-${GH_ACCOUNT}-20210908
CATEGORIES =		x11

MAINTAINER=		jcs@openbsd.org

# MIT
PERMIT_PACKAGE=	yes

WANTLIB=		X11 c Xext Xrandr

MAKE_ENV=		CC="${CC}" \
			LDFLAGS="${LDFLAGS}"
FAKE_FLAGS=		DESTDIR=""

NO_TEST=		Yes

.include <bsd.port.mk>
