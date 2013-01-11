# $OpenBSD: Makefile,v 1.160 2012/09/25 21:58:46 sthen Exp $

SHARED_ONLY=		Yes
COMMENT=		open source multi-protocol PBX (long-term support version)

VER=			1.8.19.1
DISTNAME=		asterisk-${VER:S/beta/-beta/:S/rc/-rc/}
PKGNAME=		asterisk-lts-${VER}

CATEGORIES=		telephony

HOMEPAGE=		http://www.asterisk.org/

# Mostly GPL v2 (only). "Specific permission is also granted to link
# Asterisk with OpenSSL and OpenH323 and distribute the resulting binary
# files." iLBC codec has BSD-like license terms, but also see patent
# notes in codecs/ilbc/LICENSE_ADDENDUM.
PERMIT_PACKAGE_CDROM=	patent licensing clauses
PERMIT_PACKAGE_FTP=	Yes
PERMIT_DISTFILES_CDROM= patent licensing clauses
PERMIT_DISTFILES_FTP=	Yes

WANTLIB+=		c crypto curl execinfo gsm idn iksemel
WANTLIB+=		m ogg pthread spandsp ssl stdc++ termcap
WANTLIB+=		tiff vorbis vorbisenc vorbisfile xml2 z
WANTLIB+=		${MODGETTEXT_WANTLIB}

MODULES=		devel/gettext

LIB_DEPENDS=		audio/gsm \
			audio/libogg \
			audio/libvorbis \
			devel/libexecinfo \
			graphics/tiff \
			net/curl \
			telephony/spandsp \
			textproc/iksemel \
			textproc/libxml \
			${MODGETTEXT_LIB_DEPENDS}
RUN_DEPENDS=		${MODGETTEXT_RUN_DEPENDS}
BUILD_DEPENDS=		security/libsrtp>=1.4.4 # statically linked

MASTER_SITES=		http://downloads.asterisk.org/pub/telephony/asterisk/releases/ \
			http://downloads.asterisk.org/pub/telephony/asterisk/old-releases/

EXTRACT_ONLY=		${DISTNAME}${EXTRACT_SUFX}
DISTFILES=		${DISTNAME}${EXTRACT_SUFX}

USE_GMAKE=		Yes
USE_LIBTOOL=		Yes

CONFIGURE_STYLE=	gnu
AUTOCONF_VERSION=	2.68
AUTOMAKE_VERSION=	1.10
BUILD_DEPENDS+=		${MODGNU_AUTOCONF_DEPENDS} \
			${MODGNU_AUTOMAKE_DEPENDS} \
			devel/libtool,-ltdl # bogus dependencies in menuselect

CPPFLAGS+=		-I${X11BASE}/include -I${LOCALBASE}/include
LDFLAGS+=		-L${X11BASE}/lib -L${LOCALBASE}/lib
CONFIGURE_ENV+=		CPPFLAGS="${CPPFLAGS}" \
			CFLAGS="${CFLAGS}" \
			LDFLAGS="${LDFLAGS}" \
			LIBS="-pthread"
MAKE_FLAGS+=		ASTCFLAGS="${CFLAGS}" \
			ASTLDFLAGS="${LDFLAGS}" \
			NOISY_BUILD="Yes" \
			OPTIMIZE=

CONFIGURE_ARGS+=	--with-asound=no \
			--with-avcodec=no \
			--with-cap=no \
			--with-dahdi=no \
			--with-gtk2=no \
			--with-isdnnet=no \
			--with-misdn=no \
			--with-nbs=no \
			--with-newt=no \
			--with-osptk=no \
			--with-oss=no \
			--with-pri=no \
			--with-SDL_image=no \
			--with-sdl=no \
			--with-sqlite=no \
			--with-ss7=no \
			--with-suppserv=no \
			--with-tinfo=no \
			--with-tonezone=no \
			--with-vpb=no

CONFIGURE_ARGS+=	--with-jack=no \
			--with-lua=no \
			--with-portaudio=no \
			--with-pwlib=no \
			--with-radius=no \
			--with-resample=no \
			--with-tds=no

# Some build options (including a useful malloc debug) are available
# via menuselect. They may be enabled by running 'make configure', cd
# to WRKSRC, 'gmake menuselect', then 'cd -' back to the port directory
# and 'make'.

NO_REGRESS=		Yes
INSTALL_TARGET=		install samples
EXAMPLEDIR=		${PREFIX}/share/examples/asterisk
EXAMPLEFILES=		cdr.conf extensions.ael extensions.conf logger.conf \
			modules.conf musiconhold.conf sip.conf voicemail.conf

post-patch:
	cd ${WRKSRC}; \
	    AUTOMAKE_VERSION=${AUTOMAKE_VERSION} \
	    AUTOCONF_VERSION=${AUTOCONF_VERSION} \
	    ./bootstrap.sh

post-install:
	${INSTALL_DATA_DIR} ${PREFIX}/share/doc/asterisk
	${INSTALL_DATA} ${WRKSRC}/{BUGS,CHANGES,COPYING,CREDITS} \
		${WRKSRC}/{ChangeLog,LICENSE,README*,UPGRADE*.txt} \
		${PREFIX}/share/doc/asterisk
	${INSTALL_DATA} ${WRKSRC}/doc/*.{pdf,txt,odt} \
		${PREFIX}/share/doc/asterisk
	${INSTALL_DATA_DIR} ${EXAMPLEDIR}/openbsd
.for i in ${EXAMPLEFILES}
	@${SUBST_CMD} -c ${FILESDIR}/$i.sample \
	    ${EXAMPLEDIR}/openbsd/$i.sample
.endfor
	${INSTALL_DATA} ${WRKSRC}/contrib/scripts/asterisk.ldif \
		${WRKSRC}/contrib/scripts/asterisk.ldap-schema \
		${PREFIX}/share/examples/asterisk/
	@mv ${WRKINST}/${SYSCONFDIR}/asterisk ${EXAMPLEDIR}/default
	@chown -R ${SHAREOWN}:${SHAREGRP} ${EXAMPLEDIR}
	@rm -rf ${WRKINST}/{etc,var/{log,run,spool}}/asterisk

.include <bsd.port.mk>
