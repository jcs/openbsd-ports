# $OpenBSD$

ONLY_FOR_ARCHS=	amd64 i386

COMMENT=	utility to adjust backlight on Intel video chips

CATEGORIES =	sysutils

MAINTAINER=	joshua stein <jcs@openbsd.org>

# BSD
PERMIT_PACKAGE_CDROM= Yes

GH_ACCOUNT =	jcs
GH_PROJECT =	intel_backlight_fbsd
GH_COMMIT =	a17fe19a972c3bb4020d1f2bba3aa51a9a89b99a
DISTNAME =	${GH_PROJECT:S/_fbsd//}-20160623

do-install:
	${INSTALL_PROGRAM} ${WRKBUILD}/intel_backlight ${PREFIX}/bin

.include <bsd.port.mk>
