# $OpenBSD$

SHARED_ONLY=		Yes
COMMENT=		open source Z-Wave library

DISTNAME=		openzwave-1.4.164
CATEGORIES=		comms
HOMEPAGE=		http://www.openzwave.net/

# LGPL2
PERMIT_PACKAGE_CDROM=	yes
PERMIT_PACKAGE_FTP=	yes

MASTER_SITES=		http://old.openzwave.com/downloads/

WANTLIB+=		c m pthread stdc++ usb-1.0

SHARED_LIBS=		openzwave 1.4

MODULES=		devel/gettext
LIB_DEPENDS=		devel/libusb1

USE_GMAKE=		Yes

FAKE_FLAGS=		instlibdir=${PREFIX}/lib \
			includedir=${PREFIX}/include/openzwave \
			pkgconfigdir=${PREFIX}/lib/pkgconfig \
			sysconfdir=${PREFIX}/share/openzwave \
			docdir=${PREFIX}/share/doc/openzwave \
			PREFIX=${TRUEPREFIX} \
			DOXYGEN=

MAKE_ENV=		CPPFLAGS="'-I${LOCALBASE}/include -I${LOCALBASE}/include/usb-1.0'" \
			LDFLAGS="-L${LOCALBASE}/lib -liconv -lusb-1.0" \
			${FAKE_FLAGS}

.include <bsd.port.mk>
