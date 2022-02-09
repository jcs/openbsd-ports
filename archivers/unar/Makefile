# $OpenBSD$

COMMENT		= Unarchiver for many archive formats

DISTNAME	= unar1.10.1_src
CATEGORIES	= archivers
MASTER_SITES	= http://wakaba.c3.cx/releases/TheUnarchiver/
EXTRACT_SUFX	= .zip

PKGNAME		= unarchiver-1.10.1

HOMEPAGE	= https://theunarchiver.com/

#MAINTAINER	= D5Nch3ck <d5nch3ck@disroot.org>

# LGPLv2.1
PERMIT_PACKAGE	= Yes

BUILD_DEPENDS	= audio/wavpack \
		  x11/gnustep/base

WRKDIST         = ${WRKDIR}
WRKSRC 		= ${WRKDIR}/The\ Unarchiver/XADMaster

USE_GMAKE	= YES
NO_CONFIGURE	= yes
MAKE_FILE	= Makefile.freebsd

NO_TEST         = Yes

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/??ar ${PREFIX}/bin
	${INSTALL_MAN} ${WRKSRC}/../Extra/??ar.1 ${PREFIX}/man/man1

.include <bsd.port.mk>
