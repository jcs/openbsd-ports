# $OpenBSD$

COMMENT=		proper web fonts

DISTNAME=		jcs-webfonts-1.2
REVISION=		1
CATEGORIES=		fonts

MAINTAINER=		jcs@jcs.org

PERMIT_PACKAGE_CDROM=	nope
PERMIT_PACKAGE_FTP=	nope
PERMIT_DISTFILES_FTP=	nope

MASTER_SITES=		http://jcs.org/tmp/

NO_BUILD=		Yes
NO_TEST=		Yes
PKG_ARCH=		*

TTF_INST_DIR=		${PREFIX}/share/fonts/jcs
PCF_INST_DIR=		${PREFIX}/lib/X11/fonts/jcs

do-install:
	${INSTALL_DATA_DIR} ${TTF_INST_DIR}
	cp -r ${WRKSRC}/ttf/* ${TTF_INST_DIR}/
	${INSTALL_DATA_DIR} ${PCF_INST_DIR}
	cp -r ${WRKSRC}/*.pcf* ${WRKSRC}/fonts.dir ${PCF_INST_DIR}/

.include <bsd.port.mk>
