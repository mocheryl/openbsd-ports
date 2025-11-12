COMMENT =	Go module datastore and proxy

MODGO_MODNAME =	github.com/gomods/athens
MODGO_VERSION =	v0.16.1

DISTNAME =	athens-${MODGO_VERSION}

CATEGORIES =	net

HOMEPAGE =	https://docs.gomods.io/

MAINTAINER =	Igor Zornik <mocheryl@mocheryl.org>

# MIT
PERMIT_PACKAGE =	Yes

WANTLIB +=	c pthread

MODULES =	lang/go

MODGO_LDFLAGS +=	-X github.com/gomods/athens/pkg/build.version=${MODGO_VERSION}

RUN_DEPENDS =	lang/go

# For patches to apply
WRKDIST =	${WRKSRC}

pre-configure:
	${SUBST_CMD} ${WRKDIST}/config.dev.toml ${WRKDIST}/cmd/proxy/main.go

post-build:
	@cd ${MODGO_WORKSPACE}/bin && mv proxy athens

post-install:
	${INSTALL_DATA_DIR} ${PREFIX}/share/examples/athens
	${INSTALL_DATA} ${WRKSRC}/config.dev.toml \
		${PREFIX}/share/examples/athens/config.toml
	${INSTALL_DATA} ${WRKSRC}/download.example.hcl \
		${PREFIX}/share/examples/athens/download.hcl
	${INSTALL_DATA} ${WRKSRC}/robots.txt ${FILESDIR}/home.html \
		${PREFIX}/share/examples/athens

.include "modules.inc"

.include <bsd.port.mk>
