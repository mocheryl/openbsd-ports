COMMENT =	organizer for your porn

MODGO_MODNAME =	github.com/stashapp/stash
MODGO_VERSION =	v0.27.2

DISTNAME =	stash-${MODGO_VERSION}

CATEGORIES =	multimedia

HOMEPAGE =	https://stashapp.cc/

MAINTAINER =	Igor Zornik <mocheryl@mocheryl.org>

# Distributable build generated on LMDE 6 using yarnpkg v1.22.19 and
# golang v1.23.5
# cd ui/v2.5 && yarnpkg install --frozen-lockfile
# yarnpkg run gqlgen
# mkdir -p /tmp/stash-build-${V}/{core,api}
# cp src/core/generated-*.ts /tmp/stash-build-${V}/core/
# cd ../.. && go generate ./cmd/stash
# cp internal/api/generated_*.go /tmp/stash-build-${V}/api/
# cd /tmp && tar -cvvf stash-build-${V}.tar -C /tmp stash-build-${V}
# gzip -9v stash-build-${V}.tar
DISTFILES.mocheryl =	stash-build-${MODGO_VERSION}.tar.gz
DISTFILES.gh =	stash-ui.zip

SITES.mocheryl =	https://ports.mocheryl.org/releases/
SITES.gh =	https://github.com/stashapp/stash/releases/download/${MODGO_VERSION}/

# AGPL-3.0
PERMIT_PACKAGE =	Yes

WANTLIB +=	c pthread

MODULES =	lang/go

MODGO_FLAGS +=	-tags "sqlite_stat4 sqlite_math_functions"
MODGO_LDFLAGS +=	-X github.com/stashapp/stash/internal/build.version=${MODGO_VERSION}

RUN_DEPENDS =	graphics/ffmpeg

post-extract:
	${UNZIP} -oq ${FULLDISTDIR}/stash-ui.zip -d ${WRKSRC}/ui/v2.5/build
	${GZIP_CMD} -d <${FULLDISTDIR}/stash-build-${MODGO_VERSION}.tar.gz | \
		${TAR} -xf - -C ${WRKSRC} && \
		cp ${WRKSRC}/stash-build-${MODGO_VERSION}/api/* ${WRKSRC}/internal/api/ && \
		cp ${WRKSRC}/stash-build-${MODGO_VERSION}/core/* ${WRKSRC}/ui/v2.5/src/core/		

post-install:
	${INSTALL_DATA_DIR} ${PREFIX}/share/examples/stash
	${INSTALL_DATA} -c -m 755 ${FILESDIR}/config.yml \
		${PREFIX}/share/examples/stash/config.yml
	${SUBST_CMD} ${PREFIX}/share/examples/stash/config.yml

.include "modules.inc"

.include <bsd.port.mk>
