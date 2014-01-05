# $OpenBSD$

COMMENT=		proper web fonts

DISTNAME=		jcs-webfonts-1.0
CATEGORIES=		x11

MAINTAINER=		jcs@jcs.org

PERMIT_PACKAGE_CDROM=	nope
PERMIT_PACKAGE_FTP=	nope
PERMIT_DISTFILES_FTP=	nope

MASTER_SITES=		http://jcs.org/tmp/

NO_BUILD=		Yes
NO_TEST=		Yes
PKG_ARCH=		*

INST_DIR=		${PREFIX}/lib/X11/fonts/jcs-webfonts

do-install:
	${INSTALL_DATA_DIR} ${INST_DIR}
	cp -r ${WRKSRC}/* ${INST_DIR}/

.include <bsd.port.mk>
