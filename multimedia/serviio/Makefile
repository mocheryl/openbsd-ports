# Distribution package is only prepared for these architectures
ONLY_FOR_ARCHS =	amd64

COMMENT =	free media server

V =	2.4
REVISION =	0

DISTNAME =	serviio-$V-linux
PKGNAME =	serviio-$V

CATEGORIES =	multimedia

HOMEPAGE =	https://serviio.org/

MAINTAINER =	Igor Zornik <mocheryl@mocheryl.org>

# EULA
PERMIT_PACKAGE =	https://serviio.org/licence
PERMIT_DISTFILES =	https://serviio.org/licence

SITES =	https://download.serviio.org/releases/

RUN_DEPENDS =	devel/jdk/1.8 \
				graphics/dcraw \
				graphics/ffmpeg

NO_BUILD = YES
NO_TEST = YES

# For patches to apply
WRKDIST =	${WRKDIR}

do-install:
	${INSTALL_DATA_DIR} ${PREFIX}/share/examples/serviio
.for _c in application-profiles.xml log4j2.xml profiles.xml serviio.jks
	${INSTALL_DATA} -c -m 755 ${WRKDIR}/serviio-$V/config/${_c} \
		${PREFIX}/share/examples/serviio/
.endfor
	${SUBST_CMD} ${PREFIX}/share/examples/serviio/log4j2.xml
	@rm ${PREFIX}/share/examples/serviio/log4j2.xml.beforesubst
	${INSTALL_DATA_DIR} ${PREFIX}/share/doc/serviio ${PREFIX}/serviio
.for _d in legal plugins LICENCE.txt NOTICE.txt README.txt RELEASE_NOTES.txt
	@cp -Rp ${WRKDIR}/serviio-$V/${_d} ${PREFIX}/share/doc/serviio
.endfor
	@cp -Rp ${WRKDIR}/serviio-$V/lib ${PREFIX}/serviio

.include <bsd.port.mk>
