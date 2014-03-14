# $OpenBSD: Makefile,v 1.69 2011/05/04 07:49:40 sthen Exp $

COMMENT=	tty-based e-mail client, development version

DISTNAME=	master
EXTRACT_SUFX=
PKGNAME=	mutt-jcs-1.5.21v0
WRKDIST=	${WRKDIR}/jcs-mutt-90c3eff

MAINTAINER=	jcs@openbsd.org

MASTER_SITES=	https://github.com/jcs/mutt/tarball/
DIST_SUBDIR=	mutt

CATEGORIES=	mail
HOMEPAGE=	http://www.mutt.org/

# GPLv2+
PERMIT_PACKAGE_CDROM=	Yes
PERMIT_PACKAGE_FTP=	Yes

MODULES=	devel/gettext

WANTLIB=	c crypto gssapi krb5 ssl qdbm>=14 z ncurses

AUTOCONF_VERSION= 2.65

CONFIGURE_STYLE= autoconf old
AUTOCONF_VERSION?= 2.61
CONFIGURE_ARGS= --enable-hcache \
		--enable-smtp \
		--without-gdbm \
		--enable-external_dotlock \
		--enable-flock \
		--enable-imap \
		--enable-pop \
		--disable-fcntl \
		--mandir=${PREFIX}/man \
		--sysconfdir=${CONFDIR} \
		--with-docdir="${PREFIX}/share/doc/mutt" \
		--with-gss \
		--with-ssl \
		--with-curses \
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

AUTOMAKE_VERSION= 1.9
CONFIGURE_STYLE= gnu
USE_GROFF =	Yes
BUILD_DEPENDS+=	${MODGNU_AUTOCONF_DEPENDS} \
		${MODGNU_AUTOMAKE_DEPENDS}
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
