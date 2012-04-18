# $OpenBSD$

COMMENT=		library to interface to Phidget USB devices

V=			2.1.8.20120216
SHARED_LIBS=		phidget21 0.0
DISTNAME=		libphidget-${V}
DISTFILES=		libphidget_${V}${EXTRACT_SUFX}
MASTER_SITES=		http://www.phidgets.com/downloads/libraries/

CATEGORIES=		devel

HOMEPAGE=		http://www.phidgets.com/

MAINTAINER=		joshua stein <jcs@openbsd.org>

# LGPL
PERMIT_PACKAGE_CDROM=	Yes
PERMIT_PACKAGE_FTP=	Yes
PERMIT_DISTFILES_CDROM=	Yes
PERMIT_DISTFILES_FTP=	Yes

WANTLIB=		c m usb pthread
USE_GROFF=		no

LIB_DEPENDS=		devel/libusb-compat

CONFIGURE_STYLE=	gnu
CONFIGURE_ARGS+=	CPPFLAGS="-I${LOCALBASE}/include" \
			LDFLAGS="-L${LOCALBASE}/lib -pthread" \
			--enable-jni=no \
			--enable-zeroconf=no \
			--enable-labview=no

.include <bsd.port.mk>
