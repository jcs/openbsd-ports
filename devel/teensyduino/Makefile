# $OpenBSD$

COMMENT=	libraries to run Arduino sketches on the Teensy

V=		154
DISTFILES=	Teensyduino_MacOS_Catalina.zip
PKGNAME=	teensyduino-${V}
MASTER_SITES=	https://www.pjrc.com/teensy/td_${V}/
DIST_SUBDIR=	${PKGNAME}
REVISION=	0

CATEGORIES=	devel
HOMEPAGE=	https://www.arduino.cc/

# core teensy libraries BSD and LGPLv2.1
# included individual ported libraries vary; BSD, LGPLv2.1, GPLv2, GPLv3, MIT
PERMIT_PACKAGE=	Yes

RUN_DEPENDS=	devel/arduino \
		devel/arduino-makefile \
		devel/arm-none-eabi/gcc-linaro \
		devel/arm-none-eabi/newlib \
		devel/teensyloader

NO_BUILD=       Yes
NO_TEST=	Yes
PKG_ARCH=       *

post-extract:
	find ${WRKDIR} -type f -name \*.orig -exec rm '{}' \;

do-install:
	${INSTALL_DATA_DIR} ${PREFIX}/share/arduino/hardware
	cp -r ${WRKDIR}/Teensyduino.app/Contents/Java/hardware/teensy \
		${PREFIX}/share/arduino/hardware/
	${INSTALL_DATA_DIR} \
		${PREFIX}/share/arduino/hardware/arm/arm-none-eabi/lib
	cp -r ${WRKDIR}/Teensyduino.app/Contents/Java/hardware/tools/arm/arm-none-eabi/lib \
		${PREFIX}/share/arduino/hardware/arm/arm-none-eabi/
	chown -R ${SHAREOWN}:${SHAREGRP} ${PREFIX}/share/arduino/hardware

.include <bsd.port.mk>
