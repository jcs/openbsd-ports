# $OpenBSD$

COMMENT=	CUPS printer driver for some Brother laser printers

GH_ACCOUNT=	pdewacht
GH_PROJECT=	brlaser
GH_TAGNAME=	v4

CATEGORIES=	print

# GPLv2+
PERMIT_PACKAGE_CDROM= Yes

WANTLIB+=	${COMPILER_LIBCXX} c cupsimage iconv

MODULES=	devel/cmake

LIB_DEPENDS=	print/cups,-libs

.include <bsd.port.mk>
