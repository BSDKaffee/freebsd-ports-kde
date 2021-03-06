# Created by: Henry Hu <henry.hu.sh@gmail.com>
# $FreeBSD$

PORTNAME=	ibus-libpinyin
PORTVERSION=	1.7.2
PORTREVISION=	3
CATEGORIES=	chinese
MASTER_SITES=	SF/libpinyin/${PORTNAME}

MAINTAINER=	henry.hu.sh@gmail.com
COMMENT=	Intelligent Pinyin engine based on libpinyin for IBus

LICENSE=	GPLv2

BROKEN_powerpc64=	fails to compile: PYLibPinyin.cc:222:54: 'getline' was not declared in this scope

LIB_DEPENDS=	libsqlite3.so:databases/sqlite3 \
		libibus-1.0.so:textproc/ibus \
		libpinyin.so:chinese/libpinyin

USES=		compiler:c++11-lib gmake python pkgconfig gettext
USE_GNOME=	glib20
USE_PYTHON=	py3kplist

WRKSRC=	${WRKDIR}/${DISTNAME}

GNU_CONFIGURE=	yes
CONFIGURE_ARGS=	--disable-dependency-tracking --disable-boost \
				--disable-lua-extension

OPTIONS_DEFINE=		ENGLISH STROKE OPENCC NLS
OPTIONS_DEFAULT=	ENGLISH STROKE
OPTIONS_SUB=		yes
ENGLISH_DESC=		Enable English input mode
STROKE_DESC=		Enable stroke input mode
OPENCC_DESC=		Use opencc for simplified and traditional Chinese conversion

ENGLISH_CONFIGURE_ENABLE=	english-input-mode
STROKE_CONFIGURE_ENABLE=	stroke-input-mode

OPENCC_BROKEN=			Requires newer OpenCC
OPENCC_CONFIGURE_ENABLE=	opencc
OPENCC_LIB_DEPENDS=		libopencc.so:chinese/opencc

NLS_USES=		gettext
NLS_USE=		GNOME=intltool
NLS_CONFIGURE_ENABLE=	nls

post-configure:
	@${REINPLACE_CMD} -e 's|DATADIRNAME = lib|DATADIRNAME = share|' ${WRKSRC}/po/Makefile

.include <bsd.port.mk>
