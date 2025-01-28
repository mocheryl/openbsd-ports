COMMENT =	general purpose syntax highlighter in pure Go

V =	2.15.0

DISTNAME =	chroma-${V}
PKGNAME =	go-chroma-${V}

CATEGORIES =	textproc www

HOMEPAGE =	https://github.com/alecthomas/chroma

MAINTAINER =	Igor Zornik <mocheryl@mocheryl.org>

# MIT
PERMIT_PACKAGE =	Yes

WANTLIB +=	c pthread

# cd cmd/chroma/ && go mod vendor
# cd ../chromad/ && go mod vendor
# cd .. && mkdir -p ../../chroma-${V}/cmd
# cp -r chroma chromad ../../chroma-${V}/cmd
# cd ../.. && tar -cf chroma-${V}.tar chroma-${V}
# gzip -9o chroma-${V}.tar.gz chroma-${V}.tar
SITES =	https://ports.mocheryl.org/releases/

MODGO_LDFLAGS +=	-X 'main.version=${V}'

BUILD_DEPENDS =	devel/esbuild

MODULES =	lang/go

# Rename to avoid conflict with games/chroma
pre-build:
	@mv ${WRKSRC}/cmd/chroma ${WRKSRC}/cmd/gochroma
	@mv ${WRKSRC}/cmd/chromad ${WRKSRC}/cmd/gochromad
	@esbuild --bundle ${WRKSRC}/cmd/gochromad/static/index.js --minify \
		--outfile=${WRKSRC}/cmd/gochromad/static/index.min.js
	@esbuild --bundle ${WRKSRC}/cmd/gochromad/static/index.css --minify \
		--outfile=${WRKSRC}/cmd/gochromad/static/index.min.css

do-build:
	@cd ${WRKSRC} && ${MODGO_BUILD_CMD} ./cmd/...

.include <bsd.port.mk>
