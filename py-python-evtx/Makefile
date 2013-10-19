# Created by: Antoine Brodin <antoine@FreeBSD.org>
# $FreeBSD$

PORTNAME=	python-evtx
PORTVERSION=	0.3.1
CATEGORIES=	security devel python
MASTER_SITES=	GH \
		LOCAL/antoine
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}

MAINTAINER=	antoine@FreeBSD.org
COMMENT=	Pure Python parser for recent Windows event log files

LICENSE=	AL2

USE_GITHUB=	yes
GH_ACCOUNT=	williballenthin
GH_TAGNAME=	v${PORTVERSION}
GH_COMMIT=	2b97595

USE_PYTHON=	yes
USE_PYDISTUTILS=easy_install

OPTIONS_DEFINE=	DOCS EXAMPLES

DOCSDIR=	${PREFIX}/share/doc/py-${PORTNAME}
PORTDOCS=	README.md p65-schuster.pdf

EXAMPLESDIR=	${PREFIX}/share/examples/py-${PORTNAME}
PORTEXAMPLES=	*

PLIST_FILES=	%%PYTHON_SITELIBDIR%%/%%PYEASYINSTALL_EGG%%

post-patch:
	${REINPLACE_CMD} -e 's|0\.3\.0|${PORTVERSION}|' ${WRKSRC}/Evtx/__init__.py
	${REINPLACE_CMD} -e '1s|#!.*|#!${PYTHON_CMD}|' ${WRKSRC}/scripts/*.py

NO_STAGE=	yes
.include <bsd.port.options.mk>

post-install:
.if ${PORT_OPTIONS:MDOCS}
	@${MKDIR} ${DOCSDIR} ${DOCSDIR}/html
	${INSTALL_DATA} ${WRKSRC}/README.md ${WRKSRC}/documentation/p65-schuster.pdf ${DOCSDIR}
	${INSTALL_DATA} ${WRKSRC}/documentation/html/* ${DOCSDIR}/html
.endif
.if ${PORT_OPTIONS:MEXAMPLES}
	@${MKDIR} ${EXAMPLESDIR}
	${INSTALL_SCRIPT} ${WRKSRC}/scripts/*.py ${EXAMPLESDIR}
.endif

.include <bsd.port.mk>
