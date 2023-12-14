COMMENT =	simple and extensible webmail

V =		20231123165633
MODGO_MODNAME =	git.sr.ht/~migadu/alps
MODGO_VERSION =	v0.0.0-${V}-9bf8c269a136

DISTNAME =	alps-${MODGO_VERSION}
PKGNAME =	alps-0.0.0.${V}

CATEGORIES =	mail

HOMEPAGE =	https://git.sr.ht/~migadu/alps/

MAINTAINER =	Igor Zornik <mocheryl@mocheryl.org>

# MIT
PERMIT_PACKAGE =	Yes

WANTLIB +=	c pthread

MODULES =	lang/go

# For patches to apply
WRKDIST =	${WRKSRC}

post-install:
	${INSTALL_DATA_DIR} ${PREFIX}/share/doc/alps \
		${WRKINST}${LOCALSTATEDIR}/www/alps \
		${WRKINST}${LOCALSTATEDIR}/www/alps/plugins
	@cp -Rp ${WRKSRC}/docs ${PREFIX}/share/doc/alps
	@cp -Rp ${WRKSRC}/themes ${WRKINST}${LOCALSTATEDIR}/www/alps
.for _d in base caldav carddav viewhtml
	${INSTALL_DATA_DIR} ${WRKINST}${LOCALSTATEDIR}/www/alps/plugins/${_d}
	@cp -Rp ${WRKSRC}/plugins/${_d}/public \
		${WRKINST}${LOCALSTATEDIR}/www/alps/plugins/${_d}
.endfor

.include "modules.inc"

.include <bsd.port.mk>
