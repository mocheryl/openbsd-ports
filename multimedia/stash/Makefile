COMMENT =	organizer for your porn

V =	0.31.1
MODGO_MODNAME =	github.com/stashapp/stash
MODGO_VERSION =	v${V}

DISTNAME =	stash-${MODGO_VERSION}

CATEGORIES =	multimedia

HOMEPAGE =	https://stashapp.cc/

MAINTAINER =	Igor Zornik <mocheryl@mocheryl.org>

# ftp https://github.com/stashapp/stash/archive/refs/tags/v{$V}.tar.gz
# tar xvvzf v{$V}.tar.gz
# cd stash-{$V}/ui/v2.5/ && pnpm install --frozen-lockfile
# npm run gqlgen
# mkdir -p /tmp/stash-build-${V}/{core,api}
# cp src/core/generated-*.ts /tmp/stash-build-${V}/core/
# cd .. && go generate
# cp -r login/locales /tmp/stash-build-${V}/
# cd .. && go generate ./cmd/stash
# cp internal/api/generated_*.go /tmp/stash-build-${V}/api/
# cd /tmp/ && tar -cvvf stash-build-${V}.tar stash-build-${V}
# gzip -9vo stash-build-${V}.tar.gz stash-build-${V}.tar
DISTFILES.mocheryl =	stash-build-${V}.tar.gz
DISTFILES.gh =	stash-ui-${V}{stash-ui}${EXTRACT_SUFX}

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
	${UNZIP} -oq ${FULLDISTDIR}/stash-ui-${V}${EXTRACT_SUFX} \
		-d ${WRKSRC}/ui/v2.5/build
	${GZIP_CMD} -d <${FULLDISTDIR}/stash-build-${V}.tar.gz | \
		${TAR} -xf - -C ${WRKSRC} && \
		cp ${WRKSRC}/stash-build-${V}/api/* ${WRKSRC}/internal/api/ && \
		cp ${WRKSRC}/stash-build-${V}/core/* ${WRKSRC}/ui/v2.5/src/core/ && \
		cp -r ${WRKSRC}/stash-build-${V}/locales ${WRKSRC}/ui/login/

post-install:
	${INSTALL_DATA_DIR} ${PREFIX}/share/examples/stash
	${INSTALL_DATA} ${FILESDIR}/config.yml \
		${PREFIX}/share/examples/stash/config.yml
	${SUBST_CMD} ${PREFIX}/share/examples/stash/config.yml && \
		rm ${PREFIX}/share/examples/stash/config.yml.beforesubst

.include "modules.inc"

.include <bsd.port.mk>
