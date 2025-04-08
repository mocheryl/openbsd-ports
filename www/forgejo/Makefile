COMMENT =	self-hosted lightweight version control

V =	10.0.3
DISTNAME =	forgejo-src-${V}
PKGNAME =	forgejo-${V}

SITES =	https://codeberg.org/forgejo/forgejo/releases/download/v${V}/

CATEGORIES =	www

HOMEPAGE =	https://forgejo.org/

MAINTAINER =	Igor Zornik <mocheryl@mocheryl.org>

# GPL v3+
PERMIT_PACKAGE =	Yes

WANTLIB +=	c pthread

MODULES =	lang/go

GO_TAGS =	bindata timetzdata sqlite sqlite_unlock_notify
MODGO_FLAGS +=	-tags "${GO_TAGS}"
MODGO_LDFLAGS +=	-X code.gitea.io/gitea/modules/setting.AppWorkPath=${LOCALSTATEDIR}/forgejo
MODGO_LDFLAGS +=	-X code.gitea.io/gitea/modules/setting.CustomConf=${SYSCONFDIR}/forgejo/app.ini
MODGO_LDFLAGS +=	-X code.gitea.io/gitea/modules/setting.CustomPath=${LOCALSTATEDIR}/forgejo/custom
MODGO_LDFLAGS +=	-X main.ReleaseVersion=${V}
MODGO_LDFLAGS +=	-X main.Version=${V}
MODGO_LDFLAGS +=	-X 'main.Tags=${GO_TAGS}'
MODGO_LDFLAGS +=	-X main.ForgejoVersion=${V}

RUN_DEPENDS =	devel/git-lfs

ALL_TARGET =	code.gitea.io/gitea
WRKSRC =	${MODGO_WORKSPACE}/src/${ALL_TARGET}

pre-configure:
	${SUBST_CMD} ${WRKDIST}/custom/conf/app.example.ini

post-build:
	@cd ${MODGO_WORKSPACE}/bin && mv gitea forgejo

post-install:
	${MODGO_WORKSPACE}/bin/forgejo docs --man > ${PREFIX}/man/man1/forgejo.1
	${INSTALL_DATA_DIR} ${PREFIX}/share/forgejo/conf
	${INSTALL_DATA} ${WRKSRC}/custom/conf/app.example.ini ${PREFIX}/share/forgejo/conf/

.include <bsd.port.mk>
