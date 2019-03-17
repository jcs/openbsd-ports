# $OpenBSD$

COMMENT=		BSD authentication module for duress passwords

GH_ACCOUNT=		jcs
GH_PROJECT=		login_duress
GH_TAGNAME=		v1.0

CATEGORIES=		sysutils security

MAINTAINER=		joshua stein <jcs@openbsd.org>

# BSD
PERMIT_PACKAGE_CDROM=	Yes

WANTLIB=		c util

FAKE_FLAGS=		BINDIR=${PREFIX}/libexec/auth \
			MANDIR=${PREFIX}/man/man

pre-install:
	@mkdir ${PREFIX}/libexec/auth

.include <bsd.port.mk>
