# New ports collection makefile for:	libevt
# Date created:				9 December 2012
# Whom:					antoine@FreeBSD.org
#
# $FreeBSD$
#

PORTNAME=	libevt
PORTVERSION=	20121125
CATEGORIES=	devel
MASTER_SITES=	GOOGLE_CODE
DISTNAME=	${PORTNAME}-alpha-${PORTVERSION}

MAINTAINER=	antoine@FreeBSD.org
COMMENT=	Library and tooling to access the Windows Event Log (EVT) format

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

MAN1=		evtexport.1 evtinfo.1
MAN3=		libevt.3

OPTIONS_DEFINE=	DOCS

PORTDOCS=	AUTHORS COPYING ChangeLog

.include <bsd.port.options.mk>

post-install:
.if ${PORT_OPTIONS:MDOCS}
	@${MKDIR} ${DOCSDIR}
	${INSTALL_DATA} ${PORTDOCS:S,^,${WRKSRC}/,} ${DOCSDIR}
.endif

.include <bsd.port.mk>
