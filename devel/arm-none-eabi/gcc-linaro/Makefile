# $OpenBSD$

.include "Makefile.inc"

COMMENT=	gcc for ${CONFIG} cross-development, Linaro version

PKGNAME=	${CONFIG}-gcc-linaro-${VERSION:S/-/./g}

LANGS=		c,c++

BUILD_DEPENDS+=	devel/arm-none-eabi/newlib
RUN_DEPENDS+=	devel/arm-none-eabi/newlib

CONFIGURE_ARGS+=--enable-multilib		\
		--enable-interwork		\
		--with-gmp=${LOCALBASE}		\
		--with-newlib			\
		--enable-cpp

# cope with user settings in /etc/mk.conf
MAKE_FLAGS=	LANGUAGES="c c++" CFLAGS="-I${LOCALBASE}/include"

.include <bsd.port.mk>

# The preprocessed source exceeds the suggested implementation limit
# of 256 for nesting levels of parenthesized expressions within a
# full-expression as given in Annex B of the C++ standard.
.if ${PROPERTIES:Mclang}
CXXFLAGS+=	-fbracket-depth=512
.endif
