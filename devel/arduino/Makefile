# $OpenBSD: Makefile,v 1.18 2018/09/04 12:46:10 espie Exp $

COMMENT=	open-source electronics prototyping platform

V=		1.0.6
GH_ACCOUNT=	arduino
GH_PROJECT=	arduino
GH_TAGNAME=	${V}

CATEGORIES=	devel
HOMEPAGE=	https://www.arduino.cc/

# arduino core + libraries: LGPLv2.1
# frontend application: GPLv2 (not shipped yet)
PERMIT_PACKAGE_CDROM=   Yes

RUN_DEPENDS=	devel/avr/binutils \
		devel/avr/gcc \
		devel/avr/libc \
		devel/avrdude

BUILD_DEPENDS=	archivers/unzip

NO_BUILD=       Yes
NO_TEST=	Yes
PKG_ARCH=       *
WRKDIST=	${WRKDIR}/Arduino-${V}

do-install:
	@${INSTALL_DATA_DIR} ${PREFIX}/share/{,doc,examples}/arduino
	@${SUBST_CMD} -m ${BINMODE} -c ${FILESDIR}/arduinoboot \
                ${PREFIX}/bin/arduinoboot
	@${SUBST_CMD} -m ${BINMODE} -c ${FILESDIR}/arduinoproject \
                ${PREFIX}/bin/arduinoproject
	@chown ${BINOWN}:${BINGRP} ${PREFIX}/bin/*
	@chmod ${BINMODE} ${PREFIX}/bin/*
	@${SUBST_CMD} -m 444 -c ${FILESDIR}/Makefile \
                ${PREFIX}/share/examples/arduino/Makefile
	@${SUBST_CMD} -m 444 -c ${FILESDIR}/template.ino \
                ${PREFIX}/share/examples/arduino/template.ino
	@chmod	a+r ${PREFIX}/share/examples/arduino/*
	@cp -r	${WRKSRC}/build/shared/examples/* \
		${PREFIX}/share/examples/arduino
	@cp -r	${WRKSRC}/hardware/arduino/* \
		${PREFIX}/share/arduino
	@cp -r	${WRKSRC}/libraries \
		${PREFIX}/share/arduino
	@cp -r	${WRKSRC}/{license.txt,README.md} \
		${PREFIX}/share/doc/arduino
	@unzip	-qnd ${PREFIX}/share/doc/arduino \
		${WRKSRC}/build/shared/reference.zip
	@chown -R ${SHAREOWN}:${SHAREGRP} ${PREFIX}/share
	@find ${PREFIX} -type f -name \*.orig -exec rm '{}' \;

.include <bsd.port.mk>
