# $OpenBSD$

ONLY_FOR_ARCHS=	amd64 i386

COMMENT=	utility to adjust backlight on Intel video chips

CATEGORIES =	sysutils

MAINTAINER=	joshua stein <jcs@openbsd.org>

# BSD
PERMIT_PACKAGE_CDROM= Yes

GH_ACCOUNT =	jcs
GH_PROJECT =	intel_backlight_fbsd
GH_COMMIT =	49e67dc4d55c9d1e3d4adc9b7c8e68142a8fc7a0
DISTNAME =	${GH_PROJECT:S/_fbsd//}-20170905

do-install:
	${INSTALL_PROGRAM} ${WRKBUILD}/intel_backlight ${PREFIX}/bin

.include <bsd.port.mk>
