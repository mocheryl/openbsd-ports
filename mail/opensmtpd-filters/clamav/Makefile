COMMENT =	ClamAV integration to the OpenSMTPD daemon

MODGO_MODNAME =	github.com/mocheryl/opensmtpd-filter-clamav
MODGO_VERSION =	v0.4.1

V =	0.4.1
FILTER_NAME =	clamav
DISTNAME =	filter-clamav-${MODGO_VERSION}

CATEGORIES =	mail

HOMEPAGE =	https://www.umaxx.net/

MAINTAINER =	Igor Zornik <mocheryl@mocheryl.org>

# ISC
PERMIT_PACKAGE =	Yes

# uses pledge() and unveil()
WANTLIB +=	c pthread

MODULES =	lang/go

RUN_DEPENDS =	security/clamav

post-build:
	@mv ${MODGO_WORKSPACE}/bin/opensmtpd-filter-clamav \
		${MODGO_WORKSPACE}/bin/filter-clamav

post-install:
	${INSTALL_MAN} ${WRKSRC}/filter-clamav.1 ${PREFIX}/man/man1/

.include "modules.inc"

.include <bsd.port.mk>
