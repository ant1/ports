# Created by: Jose M. Alcaide <jose@we.lc.ehu.es>
# $FreeBSD$

PORTNAME=	tcpflow
DISTVERSION=	1.4.0b1
CATEGORIES=	net
MASTER_SITES=	http://www.digitalcorpora.org/downloads/${PORTNAME}/

MAINTAINER=	antoine@FreeBSD.org
COMMENT=	Program that captures data transmitted as part of TCP connections

BUILD_DEPENDS=	${LOCALBASE}/include/boost/icl/interval.hpp:${PORTSDIR}/devel/boost-libs
LIB_DEPENDS=	cairo:${PORTSDIR}/graphics/cairo

GNU_CONFIGURE=	yes

MAN1=		tcpflow.1
PLIST_FILES=	bin/tcpflow

.include <bsd.port.mk>
