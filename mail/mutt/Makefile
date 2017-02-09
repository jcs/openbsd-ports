# $OpenBSD: Makefile,v 1.69 2011/05/04 07:49:40 sthen Exp $

COMMENT=	tty-based e-mail client, jcs branch

GH_ACCOUNT =	jcs
GH_PROJECT =	mutt
GH_COMMIT =	9cd56c72f546c677f1874086ba36a3a191323e02
DISTNAME =	${GH_PROJECT}-${GH_ACCOUNT}-1.7.2
CATEGORIES =	mail

MAINTAINER=	jcs@openbsd.org

HOMEPAGE=	http://www.mutt.org/

# GPLv2+
PERMIT_PACKAGE_CDROM=	Yes
PERMIT_PACKAGE_FTP=	Yes

MODULES=	devel/gettext

WANTLIB=	c crypto ssl qdbm>=14 z ncurses

AUTOCONF_VERSION= 2.65
AUTOMAKE_VERSION= 1.15
CONFIGURE_STYLE= gnu autoconf
USE_GROFF =	Yes

CONFIGURE_ARGS= --enable-hcache \
		--enable-sidebar \
		--disable-fcntl \
		--enable-external_dotlock \
		--enable-flock \
		--enable-imap \
		--enable-pop \
		--enable-smtp \
		--mandir=${PREFIX}/man \
		--sysconfdir=${CONFDIR} \
		--with-curses \
		--with-docdir="${PREFIX}/share/doc/mutt" \
		--with-ssl \
		--without-gdbm \
		--without-gss \
		--without-idn
FAKE_FLAGS=	sysconfdir="${PREFIX}/share/examples/mutt"

.if defined(DEBUG)
CONFIGURE_ARGS+=--enable-debug
.endif

CONFIGURE_ENV=	CPPFLAGS="-I${LOCALBASE}/include" \
		LDFLAGS="-L${LOCALBASE}/lib" \
		ISPELL="${LOCALBASE}/bin/ispell"

LIB_DEPENDS=	databases/qdbm
BUILD_DEPENDS+=	textproc/docbook \
		textproc/docbook-xsl \
		textproc/libxslt

MUTTRCDIR=	doc/

CONFDIR=	${SYSCONFDIR}/mutt
SUBST_VARS=	CONFDIR
MUTTRCDIR?=

post-patch:
	cd ${WRKSRC}; \
	    AUTOCONF_VERSION=${AUTOCONF_VERSION} \
	    AUTOMAKE_VERSION=${AUTOMAKE_VERSION} \
	    autoreconf --install

post-install:
	@mv -f ${PREFIX}/share/doc/mutt/samples/* ${PREFIX}/share/examples/mutt
	@perl -pi -e "s,/etc/Muttrc,${CONFDIR}/Muttrc," ${PREFIX}/man/man1/mutt.1
	@perl -pi -e "s,/etc/mime.types,${CONFDIR}/mime.types," ${PREFIX}/man/man1/mutt.1
	@perl -pi -e "s,/usr/bin/gpg,${LOCALBASE}/bin/gpg," \
		${PREFIX}/share/examples/mutt/gpg.rc

.include <bsd.port.mk>
