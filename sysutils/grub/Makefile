# $OpenBSD$

COMMENT=	Multiboot boot loader

DISTNAME=	grub-2.04

CATEGORIES =	sysutils

# GPLv3
PERMIT_PACKAGE=	yes

MASTER_SITES=	${MASTER_SITE_GNU:=grub/}

HOMEPAGE=	https://www.gnu.org/software/grub/

BUILD_DEPENDS=	devel/bison
MODPY_VERSION=	3.7
MODULES=	lang/python

CONFIGURE_STYLE=gnu
CONFIGURE_ENV=	YACC="bison -y"

USE_GMAKE=	yes

# Only the setjmp module needs to be compiled with gcc 8, but building
# everything with it fails assembly.  So instead of using COMPILER=ports-gcc,
# just make sure gcc 8 is installed and then build the setjmp module with egcc
BUILD_DEPENDS+= lang/gcc/8

post-configure:
	cd ${WRKDIST} && patch -p0 < ${FILESDIR}/patch-grub-core_Makefile

.include <bsd.port.mk>
