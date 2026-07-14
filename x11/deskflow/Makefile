# $OpenBSD$

COMMENT =	keyboard and mouse sharing utility

GH_ACCOUNT =	deskflow
GH_PROJECT =	deskflow
GH_TAGNAME =	v1.26.0

CATEGORIES =	x11

# GPLv2
PERMIT_PACKAGE = Yes

MODULES =	devel/cmake \
		x11/qt6

COMPILER =	base-clang ports-gcc

BUILD_DEPENDS =	x11/qt6/qttools

LIB_DEPENDS =	devel/glib2 \
		devel/gettext,-runtime \
		x11/xkbcommon

WANTLIB += ${COMPILER_LIBCXX} GL ICE Qt6Core Qt6DBus Qt6Gui
WANTLIB += Qt6Network Qt6Widgets Qt6Xml SM X11 Xext Xi Xinerama
WANTLIB += Xrandr Xtst c crypto glib-2.0 intl m pthread ssl
WANTLIB += xkbcommon xkbfile

CONFIGURE_ARGS =	-DBUILD_TESTS=OFF \
			-DBUILD_INSTALLER=OFF \
			-DBUILD_TRANSLATIONS=OFF

NO_TEST =	Yes

post-install:
	${INSTALL_DATA_DIR} ${PREFIX}/share/applications
	${INSTALL_DATA} ${WRKSRC}/deploy/linux/org.deskflow.deskflow.desktop \
		${PREFIX}/share/applications/
	${INSTALL_DATA_DIR} ${PREFIX}/share/icons/hicolor/512x512/apps
	${INSTALL_DATA} ${WRKSRC}/deploy/linux/org.deskflow.deskflow.png \
		${PREFIX}/share/icons/hicolor/512x512/apps/
	${INSTALL_DATA_DIR} ${PREFIX}/share/pixmaps
	${INSTALL_DATA} ${WRKSRC}/deploy/linux/org.deskflow.deskflow.png \
		${PREFIX}/share/pixmaps/

.include <bsd.port.mk>
