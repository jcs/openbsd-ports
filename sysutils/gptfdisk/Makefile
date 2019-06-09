# $OpenBSD$

COMMENT=	disk partitioning tool

DISTNAME=	gptfdisk-1.0.3

CATEGORIES =	sysutils

# GPLv2
PERMIT_PACKAGE_CDROM= Yes

MASTER_SITES=	${MASTER_SITE_SOURCEFORGE:=gptfdisk/}

HOMEPAGE=	http://www.rodsbooks.com/gdisk/

LIB_DEPENDS=	devel/popt \
		sysutils/e2fsprogs

MAKE_FLAGS=	CPPFLAGS+=-I${LOCALBASE}/include \
		LDFLAGS+=-L${LOCALBASE}/lib

do-install:
.for f in cgdisk gdisk sgdisk fixparts
	${INSTALL_PROGRAM} ${WRKSRC}/${f} ${PREFIX}/bin
	${INSTALL_DATA} ${WRKSRC}/${f}.8 ${PREFIX}/man/man8
.endfor

.include <bsd.port.mk>
