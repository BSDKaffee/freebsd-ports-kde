# $FreeBSD$

MASTERDIR=	${.CURDIR}/../namecoin

PKGNAMESUFFIX=	-utils

COMMENT=	Decentralized, open DNS and more (CLI and Utilities)
SLAVE_PORT=	yes

ONLY_FOR_ARCHS=	amd64 i386 ia64
ONLY_FOR_ARCHS_REASON=	does not support big-endian architectures

CONFLICTS_INSTALL=	namecoin-stable-[0-9]* namecoin-stable-daemon-[0-9]* namecoin-stable-utils-[0-9]* \
		namecoin-beta-[0-9]* namecoin-beta-daemon-[0-9]* namecoin-beta-utils-[0-9]*

OPTIONS_DEFINE=		DEBUG HARDENING TESTS
OPTIONS_DEFAULT=	HARDENING TESTS

CONFIGURE_ARGS=	--without-daemon \
		--without-gui \
		--without-libs \
		--without-qrencode \
		--with-utils \
		--disable-wallet

PLIST_FILES=	bin/namecoin-cli bin/namecoin-tx

.include "${MASTERDIR}/Makefile"
