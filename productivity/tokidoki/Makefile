COMMENT =	small and robust calendar & contacts server

V =	20241111094227

MODGO_MODNAME =	git.sr.ht/~sircmpwn/tokidoki
MODGO_VERSION =	v0.0.0-${V}-63f78d99e19d

DISTNAME =	tokidoki-${MODGO_VERSION}
PKGNAME =	tokidoki-0.0.0.${V}

CATEGORIES =	productivity

HOMEPAGE =	https://git.sr.ht/~sircmpwn/tokidoki/

MAINTAINER =	Igor Zornik <mocheryl@mocheryl.org>

# MIT
PERMIT_PACKAGE =	Yes

WANTLIB +=	c pthread

MODULES =	lang/go

BUILD_DEPENDS =	textproc/scdoc

#.if ! empty(DEBUG)
#MODGO_FLAGS +=	-tags "pam nullauth"
#.endif

post-install:
	${INSTALL_DATA_DIR} ${WRKINST}${LOCALSTATEDIR}/db/tokidoki
	@scdoc < ${WRKSRC}/doc/tokidoki.8.scd > ${PREFIX}/man/man8/tokidoki.8

.include "modules.inc"

.include <bsd.port.mk>
