COMMENT =	general purpose file previewer

MODGO_MODNAME =	github.com/doronbehar/pistol
MODGO_VERSION =	v0.5.2

DISTNAME =	pistol-${MODGO_VERSION}

CATEGORIES =	sysutils

HOMEPAGE =	https://github.com/doronbehar/pistol

MAINTAINER =	Igor Zornik <mocheryl@mocheryl.org>

# MIT
PERMIT_PACKAGE =	Yes

WANTLIB +=	c magic pthread

BUILD_DEPENDS =	textproc/asciidoctor

LIB_DEPENDS =	devel/libmagic

MODULES =	lang/go

post-install:
	@asciidoctor -b manpage -d manpage \
		${WRKSRC}/README.adoc -D ${PREFIX}/man/man1/

.include "modules.inc"

.include <bsd.port.mk>
