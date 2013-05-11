# Created by: Antoine Brodin <antoine@FreeBSD.org>
# $FreeBSD$

PORTNAME=	OleFileIO_PL
PORTVERSION=	0.24
CATEGORIES=	devel python
MASTER_SITES=	http://cdn.bitbucket.org/decalage/olefileio_pl/downloads/
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}
EXTRACT_SUFX=	.zip

MAINTAINER=	antoine@FreeBSD.org
COMMENT=	Python module to read MS OLE2 files

LICENSE=	MIT

USE_DOS2UNIX=	yes
USE_PYTHON=	yes
USE_PYDISTUTILS=yes

DOCSDIR=	${PREFIX}/share/doc/py-${PORTNAME}
PORTDOCS=	README.txt

.include <bsd.port.options.mk>

post-install:
.if ${PORT_OPTIONS:MDOCS}
	@${MKDIR} ${DOCSDIR}
	${INSTALL_DATA} ${PORTDOCS:S,^,${WRKSRC}/,} ${DOCSDIR}
.endif

.include <bsd.port.mk>
