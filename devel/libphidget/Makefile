# $OpenBSD$

COMMENT=		library to interface to Phidget USB devices

V=			2.1.8.20121218
SHARED_LIBS=		phidget21 0.0
DISTNAME=		libphidget-${V}
DISTFILES=		libphidget_${V}${EXTRACT_SUFX}
MASTER_SITES=		http://www.phidgets.com/downloads/libraries/

CATEGORIES=		devel

HOMEPAGE=		http://www.phidgets.com/

MAINTAINER=		joshua stein <jcs@openbsd.org>

# LGPL
PERMIT_PACKAGE=		Yes

WANTLIB=		c m pthread usb-1.0
MODULES=		devel/gettext

LIB_DEPENDS=		devel/libusb1

CONFIGURE_STYLE=	gnu
CONFIGURE_ARGS+=	CPPFLAGS="-I${LOCALBASE}/include" \
			LDFLAGS="-L${LOCALBASE}/lib -pthread" \
			--enable-jni=no \
			--enable-zeroconf=no \
			--enable-labview=no

.include <bsd.port.mk>
