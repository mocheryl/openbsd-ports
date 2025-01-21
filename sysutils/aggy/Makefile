COMMENT =	IPV4 subnet aggregator

MODGO_MODNAME =	github.com/mocheryl/aggy
MODGO_VERSION =	v0.3.0

DISTNAME =	aggy-${MODGO_VERSION}

CATEGORIES =	sysutils

HOMEPAGE =	https://github.com/mocheryl/aggy

MAINTAINER =	Igor Zornik <mocheryl@mocheryl.org>

# ISC
PERMIT_PACKAGE =	Yes

# uses pledge() and unveil()
WANTLIB +=	c pthread

MODULES =	lang/go

.include "modules.inc"

.include <bsd.port.mk>
