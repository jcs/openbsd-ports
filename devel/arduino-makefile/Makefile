# $OpenBSD$

COMMENT=	Makefile to build and upload Arduino sketches

V=		1.6.0
GH_ACCOUNT=	sudar
GH_PROJECT=	Arduino-Makefile
GH_TAGNAME=	${V}
PKGNAME=	arduino-makefile-${V}

CATEGORIES=	devel

# LGPL
PERMIT_PACKAGE_CDROM=   Yes

RUN_DEPENDS=	devel/arduino \
		devel/gmake \
		devel/py-serial

NO_BUILD=       Yes
NO_TEST=	Yes
PKG_ARCH=       *

do-install:
	${INSTALL_DATA_DIR} ${PREFIX}/share/arduino-makefile
	cp -r ${WRKDIST}/*.mk ${PREFIX}/share/arduino-makefile/
	${INSTALL_SCRIPT} ${WRKDIST}/bin/ard-reset-arduino ${PREFIX}/bin
	${INSTALL_SCRIPT} ${WRKDIST}/bin/robotis-loader ${PREFIX}/bin
	${INSTALL_MAN} ${WRKDIST}/ard-reset-arduino.1 ${PREFIX}/man/man1
	${INSTALL_MAN} ${WRKDIST}/robotis-loader.1 ${PREFIX}/man/man1
	${INSTALL_DATA_DIR} ${PREFIX}/share/examples/arduino-makefile
	cp -r ${WRKDIST}/examples/* ${PREFIX}/share/examples/arduino-makefile/
	find ${PREFIX} -type f -name \*.orig -exec rm '{}' \;

.include <bsd.port.mk>
