# Created by: Antoine Brodin <antoine@FreeBSD.org>
# $FreeBSD$

PORTNAME=	colorize
PORTVERSION=	1.0
CATEGORIES=	graphics

MAINTAINER=	antoine@FreeBSD.org
COMMENT=	Tools for visualizing data and comparing files

LICENSE=	GPLv3

USE_GITHUB=	yes
GH_ACCOUNT=	jessek
GH_COMMIT=	5d9a46d

USE_AUTOTOOLS=	autoconf autoheader automake aclocal
AUTOMAKE_ARGS=	--add-missing

PLIST_FILES=	bin/colorize bin/filecompare

PORTDOCS=	AUTHORS ChangeLog

.include <bsd.port.options.mk>

post-install:
.if ${PORT_OPTIONS:MDOCS}
	@${MKDIR} ${DOCSDIR}
	${INSTALL_DATA} ${PORTDOCS:S,^,${WRKSRC}/,} ${DOCSDIR}
.endif

.include <bsd.port.mk>
