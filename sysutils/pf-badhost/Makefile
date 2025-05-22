COMMENT =	fast, bi-directional network filtering utility

V =	0.5
REVISION =	0

DISTNAME =	pf-badhost-${V}

CATEGORIES =	sysutils

HOMEPAGE =	https://www.geoghegan.ca/pfbadhost.html

MAINTAINER =	Igor Zornik <mocheryl@mocheryl.org>

# ISC
PERMIT_PACKAGE =	Yes

# mkdir -p pf-badhost-0.5/install pf-badhost-0.5/man && cd pf-badhost-0.5
# ftp https://www.geoghegan.ca/pub/pf-badhost/0.5/pf-badhost.sh
# ftp -o install/openbsd.txt \
# 	https://www.geoghegan.ca/pub/pf-badhost/0.5/install/openbsd.txt
# ftp -o man/man.txt https://www.geoghegan.ca/pub/pf-badhost/0.5/man/man.txt
# cd .. && tar -cf pf-badhost-0.5.tar pf-badhost-0.5
# gzip -9o pf-badhost-0.5.tar.gz pf-badhost-0.5.tar
SITES =	https://ports.mocheryl.org/releases/

NO_BUILD =	Yes

do-install:
	${INSTALL_SCRIPT} ${WRKSRC}/pf-badhost.sh ${PREFIX}/bin/pf-badhost
	${INSTALL_DATA_DIR} ${PREFIX}/share/doc/pf-badhost \
		${WRKINST}${LOCALSTATEDIR}/log/pf-badhost
	@cp -p ${WRKSRC}/man/man.txt ${WRKSRC}/install/openbsd.txt \
		${PREFIX}/share/doc/pf-badhost
	${INSTALL_DATA} /dev/null ${WRKINST}${SYSCONFDIR}/pf-badhost.txt
	${INSTALL_DATA} /dev/null \
		${WRKINST}${LOCALSTATEDIR}/log/pf-badhost/pf-badhost.log
	${INSTALL_DATA} /dev/null \
		${WRKINST}${LOCALSTATEDIR}/log/pf-badhost/pf-badhost.log.0.gz

# Syntax check all scripts
do-test:
	@find ${WRKSRC} -type f -name \*.sh -exec sh -n {} \;

.include <bsd.port.mk>
