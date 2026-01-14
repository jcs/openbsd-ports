# $OpenBSD$

COMMENT=	implementation of the SSL/TLS protocol

V=		0.6
DISTNAME=	bearssl-${V}
CATEGORIES=	security
HOMEPAGE=	https://www.bearssl.org/

SHARED_LIBS +=	bearssl 0.6

# MIT
PERMIT_PACKAGE=	yes

SITES=		${HOMEPAGE}

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/build/brssl ${PREFIX}/bin
	${INSTALL_DATA} ${WRKSRC}/build/libbearssl.so \
		${PREFIX}/lib/libbearssl.so.${LIBbearssl_VERSION}
	${INSTALL_DATA} ${WRKSRC}/build/libbearssl.a ${PREFIX}/lib/
	@mkdir -p ${PREFIX}/include/bearssl
	@cp -R ${WRKSRC}/inc/* ${PREFIX}/include/bearssl/

.include <bsd.port.mk>
