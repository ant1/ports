# New ports collection makefile for:	liblnk
# Date created:				30 November 2012
# Whom:					antoine@FreeBSD.org
#
# $FreeBSD$
#

PORTNAME=	liblnk
PORTVERSION=	20121205
CATEGORIES=	devel
MASTER_SITES=	GOOGLE_CODE
DISTNAME=	${PORTNAME}-alpha-${PORTVERSION}

MAINTAINER=	antoine@FreeBSD.org
COMMENT=	Library and tools to access the Windows Shortcut File (LNK) Format

LICENSE=	LGPL3

USE_GETTEXT=	yes
USE_GNOME=	gnomehack
USE_ICONV=	yes
USE_LDCONFIG=	yes
USE_PYTHON=	yes

GNU_CONFIGURE=	yes
CONFIGURE_ARGS=	--enable-python
LDFLAGS+=	-L${LOCALBASE}/lib
WRKSRC=		${WRKDIR}/${PORTNAME}-${PORTVERSION}

MAN1=		lnkinfo.1
MAN3=		liblnk.3

OPTIONS_DEFINE=	DOCS

PORTDOCS=	AUTHORS COPYING ChangeLog

.include <bsd.port.options.mk>

post-install:
.if ${PORT_OPTIONS:MDOCS}
	@${MKDIR} ${DOCSDIR}
	${INSTALL_DATA} ${PORTDOCS:S,^,${WRKSRC}/,} ${DOCSDIR}
.endif

.include <bsd.port.mk>
