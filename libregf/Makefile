# New ports collection makefile for:	libregf
# Date created:				9 December 2012
# Whom:					antoine@FreeBSD.org
#
# $FreeBSD$
#

PORTNAME=	libregf
PORTVERSION=	20121112
CATEGORIES=	devel
MASTER_SITES=	GOOGLE_CODE
DISTNAME=	${PORTNAME}-alpha-${PORTVERSION}

MAINTAINER=	antoine@FreeBSD.org
COMMENT=	Library and tools to support the Windows NT Registry File format

LICENSE=	LGPL3

LIB_DEPENDS=	fuse:${PORTSDIR}/sysutils/fusefs-libs

USE_GETTEXT=	yes
USE_GNOME=	gnomehack
USE_ICONV=	yes
USE_LDCONFIG=	yes
USE_PYTHON=	yes

GNU_CONFIGURE=	yes
CONFIGURE_ARGS=	--enable-python
LDFLAGS+=	-L${LOCALBASE}/lib
WRKSRC=		${WRKDIR}/${PORTNAME}-${PORTVERSION}

MAN1=		regfinfo.1
MAN3=		libregf.3

OPTIONS_DEFINE=	DOCS

PORTDOCS=	AUTHORS COPYING ChangeLog

.include <bsd.port.pre.mk>

.if ${OSVERSION} < 1000020
RUN_DEPENDS+=	${LOCALBASE}/modules/fuse.ko:${PORTSDIR}/sysutils/fusefs-kmod
.endif

post-install:
.if ${PORT_OPTIONS:MDOCS}
	@${MKDIR} ${DOCSDIR}
	${INSTALL_DATA} ${PORTDOCS:S,^,${WRKSRC}/,} ${DOCSDIR}
.endif

.include <bsd.port.post.mk>
