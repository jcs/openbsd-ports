# $OpenBSD$

COMMENT=	gem for implementing OAuth clients and servers

DISTNAME=	oauth-0.3.6
CATEGORIES=	security net

HOMEPAGE=	http://oauth.rubyforge.org/

# MIT
PERMIT_PACKAGE=	yes

BUILD_DEPENDS=	${RUN_DEPENDS}
RUN_DEPENDS=	security/ruby-hmac,${MODRUBY_FLAVOR}

MODULES=	lang/ruby
CONFIGURE_STYLE= ruby gem

.include <bsd.port.mk>
