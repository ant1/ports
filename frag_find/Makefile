# Created by: Antoine Brodin <antoine@FreeBSD.org>
# $FreeBSD$

PORTNAME=	frag_find
PORTVERSION=	1.0.0
CATEGORIES=	sysutils
MASTER_SITES=	http://www.digitalcorpora.org/downloads/${PORTNAME}/

MAINTAINER=	antoine@FreeBSD.org
COMMENT=	Hash-based carver tool

LICENSE=	GPLv2

LIB_DEPENDS=	afflib:${PORTSDIR}/sysutils/afflib \
		expat:${PORTSDIR}/textproc/expat2

GNU_CONFIGURE=	yes
CPPFLAGS+=	-I${LOCALBASE}/include
LDFLAGS+=	-L${LOCALBASE}/lib

.include <bsd.port.mk>
