# Created by: Antoine Brodin <antoine@FreeBSD.org>
# $FreeBSD$

PORTNAME=	python-evtx
DISTVERSION=	0.1
CATEGORIES=	security devel python
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}

MAINTAINER=	antoine@FreeBSD.org
COMMENT=	Pure Python parser for recent Windows event log files

LICENSE=	AL2

USE_GITHUB=	yes
GH_ACCOUNT=	williballenthin
GH_TAGNAME=	v${DISTVERSION}
GH_COMMIT=	43980e8

USE_PYTHON=	yes
USE_PYDISTUTILS=easy_install
PYDISTUTILS_PKGNAME=Evtx

OPTIONS_DEFINE=	DOCS EXAMPLES

DOCSDIR=	${PREFIX}/share/doc/py-${PORTNAME}
PORTDOCS=	README.md p65-schuster.pdf
PORTEXAMPLES=	*

post-patch:
	${REINPLACE_CMD} -e 's|]|], zip_safe=False|' ${WRKSRC}/setup.py
	${REINPLACE_CMD} -i '' -e 's|/bin/python|${PYTHON_CMD}|' ${WRKSRC}/scripts/*

.include <bsd.port.options.mk>

post-install:
.if ${PORT_OPTIONS:MDOCS}
	@${MKDIR} ${DOCSDIR}
	${INSTALL_DATA} ${WRKSRC}/README.md ${WRKSRC}/documentation/p65-schuster.pdf ${DOCSDIR}
.endif
.if ${PORT_OPTIONS:MEXAMPLES}
	@${MKDIR} ${EXAMPLESDIR}
	${INSTALL_SCRIPT} ${WRKSRC}/scripts/* ${EXAMPLESDIR}
.endif

.include <bsd.port.mk>
