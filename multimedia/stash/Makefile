COMMENT =	organizer for your porn

MODGO_MODNAME =	github.com/stashapp/stash
MODGO_VERSION =	v0.30.1

DISTNAME =	stash-${MODGO_VERSION}

CATEGORIES =	multimedia

HOMEPAGE =	https://stashapp.cc/

MAINTAINER =	Igor Zornik <mocheryl@mocheryl.org>

# ftp https://github.com/stashapp/stash/archive/refs/tags/v{$V}.tar.gz
# tar xvvzf v{$V}.tar.gz
# cd stash-{$V}/ui/v2.5/ && pnpm install --frozen-lockfile
# npm run gqlgen
# mkdir -p /tmp/stash-build-v${V}/{core,api}
# cp src/core/generated-*.ts /tmp/stash-build-v${V}/core/
# cd .. && go generate
# cp -r login/locales /tmp/stash-build-v0.30.1/
# cd .. && go generate ./cmd/stash
# cp internal/api/generated_*.go /tmp/stash-build-v${V}/api/
# cd /tmp/ && tar -cvvf stash-build-v${V}.tar stash-build-v${V}
# gzip -9vo stash-build-v${V}.tar.gz stash-build-v${V}.tar
DISTFILES.mocheryl =	stash-build-${MODGO_VERSION}.tar.gz
DISTFILES.gh =	stash-ui.zip

SITES.mocheryl =	https://ports.mocheryl.org/releases/
SITES.gh =	https://github.com/stashapp/stash/releases/download/${MODGO_VERSION}/

# AGPL-3.0
PERMIT_PACKAGE =	Yes

WANTLIB +=	c m pthread

MODULES =	lang/go

MODGO_FLAGS +=	-tags "sqlite_stat4 sqlite_math_functions"
MODGO_LDFLAGS +=	-X github.com/stashapp/stash/internal/build.version=${MODGO_VERSION}

RUN_DEPENDS =	graphics/ffmpeg

post-extract:
	${UNZIP} -oq ${FULLDISTDIR}/stash-ui.zip -d ${WRKSRC}/ui/v2.5/build
	${GZIP_CMD} -d <${FULLDISTDIR}/stash-build-${MODGO_VERSION}.tar.gz | \
		${TAR} -xf - -C ${WRKSRC} && \
		cp ${WRKSRC}/stash-build-${MODGO_VERSION}/api/* ${WRKSRC}/internal/api/ && \
		cp ${WRKSRC}/stash-build-${MODGO_VERSION}/core/* ${WRKSRC}/ui/v2.5/src/core/ && \
		cp -r ${WRKSRC}/stash-build-${MODGO_VERSION}/locales ${WRKSRC}/ui/login/

post-install:
	${INSTALL_DATA_DIR} ${PREFIX}/share/examples/stash
	${INSTALL_DATA} -c -m 755 ${FILESDIR}/config.yml \
		${PREFIX}/share/examples/stash/config.yml
	${SUBST_CMD} ${PREFIX}/share/examples/stash/config.yml

.include "modules.inc"

.include <bsd.port.mk>
