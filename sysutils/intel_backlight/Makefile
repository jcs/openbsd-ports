# $OpenBSD$

ONLY_FOR_ARCHS=	amd64 i386

COMMENT=	utility to adjust backlight on Intel video chips

CATEGORIES =	sysutils

MAINTAINER=	joshua stein <jcs@openbsd.org>

# BSD
PERMIT_PACKAGE_CDROM= Yes

GH_ACCOUNT =	jcs
GH_PROJECT =	intel_backlight_fbsd
GH_COMMIT =	1d9432b97202728e53b0f7ef0f2a5c15aeaf5b80
DISTNAME =	${GH_PROJECT:S/_fbsd//}-20160623p0

do-install:
	${INSTALL_PROGRAM} ${WRKBUILD}/intel_backlight ${PREFIX}/bin

.include <bsd.port.mk>
