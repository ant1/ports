# New ports collection makefile for:	libmsiecf
# Date created:				9 December 2012
# Whom:					antoine@FreeBSD.org
#
# $FreeBSD$
#

PORTNAME=	libmsiecf
PORTVERSION=	20120428
CATEGORIES=	devel
MASTER_SITES=	GOOGLE_CODE
DISTNAME=	${PORTNAME}-alpha-${PORTVERSION}

MAINTAINER=	antoine@FreeBSD.org
COMMENT=	Library and tools to access the MSIE index.dat files

LICENSE=	LGPL3

USE_GETTEXT=	yes
USE_GNOME=	gnomehack
USE_ICONV=	yes
USE_LDCONFIG=	yes

GNU_CONFIGURE=	yes
LDFLAGS+=	-L${LOCALBASE}/lib
WRKSRC=		${WRKDIR}/${PORTNAME}-${PORTVERSION}

MAN1=		msiecfexport.1 msiecfinfo.1
MAN3=		libmsiecf.3

OPTIONS_DEFINE=	DOCS

PORTDOCS=	AUTHORS COPYING ChangeLog

.include <bsd.port.options.mk>

post-install:
.if ${PORT_OPTIONS:MDOCS}
	@${MKDIR} ${DOCSDIR}
	${INSTALL_DATA} ${PORTDOCS:S,^,${WRKSRC}/,} ${DOCSDIR}
.endif

.include <bsd.port.mk>
