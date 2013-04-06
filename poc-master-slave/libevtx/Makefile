# Created by: Antoine Brodin <antoine@FreeBSD.org>
# $FreeBSD: head/devel/libevtx/Makefile 315434 2013-03-28 04:47:09Z miwi $

PORTNAME=	libevtx
DISTVERSION=	alpha-20130319
CATEGORIES?=	devel
MASTER_SITES=	GOOGLE_CODE

MAINTAINER=	antoine@FreeBSD.org
COMMENT?=	Library and tooling to access the Windows XML Event Log (EVTX) format

LICENSE=	LGPL3

GNU_CONFIGURE=	yes
USE_GETTEXT=	yes
USES=		pathfix
USE_ICONV=	yes
USE_LDCONFIG=	yes

LDFLAGS+=	-L${LOCALBASE}/lib
WRKSRC=		${WRKDIR}/${PORTNAME}-${PORTVERSION:E}

.if !defined(LIBEVTX_SLAVE)
MAN1=		evtxinfo.1
MAN3=		libevtx.3
.endif

OPTIONS_DEFINE?=DOCS EXAMPLES

.if !defined(LIBEVTX_SLAVE)
PORTDOCS=	AUTHORS ChangeLog
.endif
PORTEXAMPLES=	*
EXAMPLESSRC?=	${PORTNAME}

.include <bsd.port.options.mk>

post-install:
.if !defined(LIBEVTX_SLAVE) && ${PORT_OPTIONS:MDOCS}
	@${MKDIR} ${DOCSDIR}
	${INSTALL_DATA} ${PORTDOCS:S,^,${WRKSRC}/,} ${DOCSDIR}
.endif
.if ${PORT_OPTIONS:MEXAMPLES}
	@${MKDIR} ${EXAMPLESDIR}
	${INSTALL_DATA} ${WRKSRC}/examples/${EXAMPLESSRC}/* ${EXAMPLESDIR}
.endif

.include <bsd.port.mk>
