# $OpenBSD$

COMMENT=		free open source disk encryption software

V=			1.22
PKGNAME=		veracrypt-${V}
CATEGORIES=		security
HOMEPAGE=		https://www.veracrypt.fr/

# Apache2
PERMIT_PACKAGE_CDROM=	yes
PERMIT_PACKAGE_FTP=	yes

MASTER_SITES=		https://launchpad.net/veracrypt/trunk/${V}/+download/
DISTNAME=		VeraCrypt_${V}_Source
EXTRACT_SUFX=		.tar.bz2

WANTLIB +=		${COMPILER_LIBCXX} fuse

BUILD_DEPENDS=		devel/yasm \
			sysutils/coreutils
LIB_DEPENDS=		x11/wxWidgets

WRKDIST=		${WRKDIR}/src
USE_GMAKE=		Yes
ALL_TARGET=		NOGUI=1 NOTEST=1

post-extract:
	@cp -r ${FILESDIR}/OpenBSD ${WRKDIST}/Core/Unix/

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/Main/veracrypt ${PREFIX}/bin

.include <bsd.port.mk>
