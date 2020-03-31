# $OpenBSD$

.include "../gcc-linaro/Makefile.inc"

COMMENT=	${CONFIG} cross-development bootstrap, Linaro version

PKGNAME=	${CONFIG}-gcc-linaro-bootstrap-${VERSION:S/-/./g}

LANGS=		c

CONFIGURE_ARGS+=--without-headers \
		--exec-prefix=${PREFIX}/${CONFIG}/bootstrap \
		--with-local-prefix=${PREFIX}/${CONFIG}/bootstrap \
		--with-as=${LOCALBASE}/bin/${CONFIG}-as \
		--with-ld=${LOCALBASE}/bin/${CONFIG}-ld

# cope with user settings in /etc/mk.conf
MAKE_FLAGS=	LANGUAGES="c" CFLAGS="-I${LOCALBASE}/include"

.include <bsd.port.mk>

# The preprocessed source exceeds the suggested implementation limit
# of 256 for nesting levels of parenthesized expressions within a
# full-expression as given in Annex B of the C++ standard.
.if ${PROPERTIES:Mclang}
CXXFLAGS+=	-fbracket-depth=512
.endif
