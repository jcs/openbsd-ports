# $OpenBSD: Makefile,v 1.69 2011/05/04 07:49:40 sthen Exp $

COMMENT=	tty-based e-mail client, development version

CATEGORIES=	mail

DISTNAME=	mutt-1.5.21
EPOCH=		0

MAINTAINER=	Stuart Henderson <sthen@openbsd.org>

MASTER_SITES=	${MASTER_SITE_SOURCEFORGE:=mutt/} \
		${MASTER_SITES_MUTT:=devel/}
MASTER_SITES_MUTT= ftp://ftp.mutt.org/mutt/ \
		   ftp://ftp.fu-berlin.de/pub/unix/mail/mutt/ \
		   ftp://ftp.gbnet.net/pub/mutt-international/ \
		   ftp://ftp.gwdg.de/pub/unix/mail/mutt/international/

MASTER_SITES0=	http://www.spinnaker.de/mutt/compressed/
MASTER_SITES1=	http://lunar-linux.org/~tchan/mutt/
MASTER_SITES2=	http://spacehopper.org/mutt/
MASTER_SITES3=	http://jcs.org/tmp/
DIST_SUBDIR=	mutt

HOMEPAGE=	http://www.mutt.org/

# GPLv2+
PERMIT_PACKAGE_CDROM=	Yes
PERMIT_PACKAGE_FTP=	Yes
PERMIT_DISTFILES_CDROM=	Yes
PERMIT_DISTFILES_FTP=	Yes

MODULES=	devel/gettext

WANTLIB=	c crypto gssapi krb5 ssl qdbm>=14 z 

FLAVORS=	idn jcs sasl sidebar slang mixmaster compressed
FLAVOR?=

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
		--with-ssl
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

.if ${FLAVOR:L:Msasl}
CONFIGURE_ARGS+= --with-sasl=${LOCALBASE}
LIB_DEPENDS+=	security/cyrus-sasl2
WANTLIB+=	sasl2
.endif

MUTTRCDIR=	doc/

DIST_COMPRESSED=compressed-5302767aa6aa.gz:2
DIST_SIDEBAR=	sidebar-5302767aa6aa.gz:2
DIST_JCS=	mutt-jcs-patches-openbsd.diff:3

.if ${FLAVOR:L:Msidebar}
PATCHFILES+=		${DIST_SIDEBAR}
PATCH_DIST_STRIP=	-p1
.else
SUPDISTFILES+=		${DIST_SIDEBAR}
.endif

.if ${FLAVOR:L:Mjcs}
PATCHFILES+=		${DIST_JCS}
PATCH_DIST_STRIP=	-p1
.else
SUPDISTFILES+=		${DIST_JCS}
.endif

.if ${FLAVOR:L:Mslang}
LIB_DEPENDS+=		devel/libslang
CONFIGURE_ARGS+=	--with-slang="${PREFIX}"
WANTLIB+=		m termlib slang>=14
.else
CONFIGURE_ARGS+=	--with-curses
WANTLIB+=		ncurses 
.endif

# compressed folder support
DIST_COMPRESSED?=	patch-${VERSION}.rr.compressed.1.gz:0
.if ${FLAVOR:L:Mcompressed}
PATCHFILES+=		${DIST_COMPRESSED}
PATCH_DIST_STRIP=	-p1
CONFIGURE_ARGS+=	--enable-compressed
.else
SUPDISTFILES+=		${DIST_COMPRESSED}
.endif

.if ${FLAVOR:L:Mmixmaster}
CONFIGURE_ARGS+=	--with-mixmaster="${LOCALBASE}/sbin/mixmaster"
RUN_DEPENDS+=		mail/mixmaster
.endif

.if ${FLAVOR:L:Midn}
CONFIGURE_ARGS+=	--with-idn
LIB_DEPENDS+=		devel/libidn
WANTLIB+=		idn>=16
.else
CONFIGURE_ARGS+=	--without-idn
.endif

.if ${FLAVOR:L:Mjcs}
PATCHFILES+=		${DIST_COMPRESSED}
PATCH_DIST_STRIP=	-p1
CONFIGURE_ARGS+=	--enable-compressed
.else
SUPDISTFILES+=		${DIST_COMPRESSED}
.endif

.if defined(HOMESPOOL)
CONFIGURE_ARGS+=	--with-homespool="${HOMESPOOL}"
.endif

.if defined(DOMAIN)
CONFIGURE_ARGS+=	--with-domain="${DOMAIN}"
.endif

WRKDIST=	${WRKDIR}/${DISTNAME:S/i$//}
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
