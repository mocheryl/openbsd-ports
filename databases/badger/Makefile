COMMENT =	tools to manage Badger database

MODGO_MODNAME =	github.com/dgraph-io/badger/v4
MODGO_VERSION =	v4.7.0

DISTNAME =	badger-${MODGO_VERSION}

CATEGORIES =	databases

HOMEPAGE =	https://docs.hypermode.com/badger

MAINTAINER =	Igor Zornik <mocheryl@mocheryl.org>

# apache 2.0
PERMIT_PACKAGE =	Yes

WANTLIB +=	c pthread

MODULES =	lang/go

ALL_TARGET =	./badger/...

.include "modules.inc"

.include <bsd.port.mk>
