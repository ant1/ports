# New ports collection makefile for:	pytsk
# Date created:				10 December 2012
# Whom:					antoine@FreeBSD.org
#
# $FreeBSD$
#

PORTNAME=	pytsk
PORTVERSION=	20121110
CATEGORIES=	devel python
MASTER_SITES=	GOOGLE_CODE
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}
DISTNAME=	${PORTNAME}-2012-11-10
EXTRACT_SUFX=	.tgz

MAINTAINER=	antoine@FreeBSD.org
COMMENT=	Python bindings for the Sleuthkit

LICENSE=	AL2

LIB_DEPENDS=	tsk3:${PORTSDIR}/sysutils/sleuthkit

WRKSRC=		${WRKDIR}/${PORTNAME}

USE_PYTHON=	yes
USE_PYDISTUTILS=yes
PYDISTUTILS_PKGNAME=pytsk3
PYDISTUTILS_PKGVERSION=0.1

# Todo:
# - misc.h doesn't include <sys/types.h> early enough
# - CPPFLAGS and LDFLAGS need to be adjusted (setup.py)
# - PORTDOCS=LICENSE README

.include <bsd.port.mk>
