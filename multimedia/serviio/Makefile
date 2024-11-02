# Distribution package is only prepared for these architectures
ONLY_FOR_ARCHS =	amd64

COMMENT =	free media server

V =	2.4

DISTNAME =	serviio-$V-linux
PKGNAME =	serviio-$V

CATEGORIES =	multimedia

HOMEPAGE =	https://serviio.org/

MAINTAINER =	Igor Zornik <mocheryl@mocheryl.org>

# EULA
PERMIT_PACKAGE =	https://serviio.org/licence
PERMIT_DISTFILES =	https://serviio.org/licence

SITES =	https://download.serviio.org/releases/

RUN_DEPENDS =	graphics/dcraw \
				graphics/ffmpeg \
				devel/jdk/1.8

NO_BUILD = YES
NO_TEST = YES

do-install:
	${INSTALL_DATA_DIR} ${PREFIX}/share/doc/serviio ${PREFIX}/serviio
.for _d in legal plugins LICENCE.txt NOTICE.txt README.txt RELEASE_NOTES.txt
	@cp -Rp ${WRKDIR}/serviio-$V/${_d} ${PREFIX}/share/doc/serviio
.endfor
.for _d in config lib library
	@cp -Rp ${WRKDIR}/serviio-$V/${_d} ${PREFIX}/serviio
.endfor

.include <bsd.port.mk>
