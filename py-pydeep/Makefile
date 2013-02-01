# Created by: Antoine Brodin <antoine@FreeBSD.org>
# $FreeBSD$

PORTNAME=	pydeep
PORTVERSION=	0.2
CATEGORIES=	security devel python
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}

MAINTAINER=	antoine@FreeBSD.org
COMMENT=	Python bindings for ssdeep

LICENSE=	BSD

LIB_DEPENDS=	fuzzy:${PORTSDIR}/security/ssdeep

USE_GITHUB=	yes
GH_ACCOUNT=	kbandla
GH_TAGNAME=	4aabf0866c8c53973211733d223dfc7c3395381e
GH_COMMIT=	4aabf08

USE_PYTHON=	yes
USE_PYDISTUTILS=yes

OPTIONS_DEFINE=	DOCS

DOCSDIR=	${PREFIX}/share/doc/py-${PORTNAME}
PORTDOCS=	README

post-patch:
	${REINPLACE_CMD} -e 's|name = "pydeep",|name = "pydeep", version="${PORTVERSION}",|'\
		-e 's|libraries = \["fuzzy"],|libraries = ["fuzzy"], include_dirs = ["${LOCALBASE}/include"], library_dirs = ["${LOCALBASE}/lib"],|' \
		${WRKSRC}/setup.py

.include <bsd.port.options.mk>

post-install:
.if ${PORT_OPTIONS:MDOCS}
	@${MKDIR} ${DOCSDIR}
	${INSTALL_DATA} ${PORTDOCS:S,^,${WRKSRC}/,} ${DOCSDIR}
.endif

.include <bsd.port.mk>
