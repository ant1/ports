# Created by: antoine@FreeBSD.org
# $FreeBSD$

PORTNAME=	registrydecoder
PORTVERSION=	r105
CATEGORIES=	security
MASTER_SITES=	LOCAL/antoine

MAINTAINER=	antoine@FreeBSD.org
COMMENT=	Automated acquisition, analysis, and reporting of registry contents

LICENSE=	GPLv2

RUN_DEPENDS=	libewf>=0:${PORTSDIR}/devel/libewf \
		${PYTHON_PKGNAMEPREFIX}pytsk>=0:${PORTSDIR}/devel/py-pytsk \
		${PYTHON_PKGNAMEPREFIX}qt4-core>=0:${PORTSDIR}/devel/py-qt4-core \
		${PYTHON_PKGNAMEPREFIX}qt4-gui>=0:${PORTSDIR}/x11-toolkits/py-qt4-gui \
		${PYTHON_PKGNAMEPREFIX}qt4-network>=0:${PORTSDIR}/net/py-qt4-network \
		reglookup>=0:${PORTSDIR}/devel/reglookup \
		${PYTHON_PKGNAMEPREFIX}reportlab>=0:${PORTSDIR}/print/py-reportlab \
		${PYTHON_PKGNAMEPREFIX}sqlite3>=0:${PORTSDIR}/databases/py-sqlite3 \
		${PYTHON_PKGNAMEPREFIX}xlwt>=0:${PORTSDIR}/textproc/py-xlwt

USE_PYTHON=	yes

SUB_FILES=	${PORTNAME}.sh
SUB_LIST=	PYTHON_CMD=${PYTHON_CMD} PATH=${PYTHONPREFIX_SITELIBDIR}/${PORTNAME}

post-patch:
	${REINPLACE_CMD} -e 's/"template_manager"./"template_manager",/' ${WRKSRC}/__init__.py

do-build:
	${MKDIR} ${WRKSRC}/build
.for f in __init__.py cleanwindows.py common.py errorclasses.py guicontroller.py guimain.py opencase.py report_manager.py start_processing.py template_manager.py
	${CP} ${WRKSRC}/${f} ${WRKSRC}/build/${f}
.endfor
	${CP} ${FILESDIR}/ewf.py ${WRKSRC}/build/ewf.py
.for d in GUI acquirefiles datastructures initial_processing pyinstaller registryparser reporting templates
	${MKDIR} ${WRKSRC}/build/${d}
	(cd ${WRKSRC}/${d} && ${COPYTREE_SHARE} \* ${WRKSRC}/build/${d})
.endfor
	${PYTHON_CMD} -m compileall ${WRKSRC}/build
	${PYTHON_CMD} -O -m compileall ${WRKSRC}/build

do-install:
	${MKDIR} ${PYTHONPREFIX_SITELIBDIR}/${PORTNAME}
	(cd ${WRKSRC}/build && ${COPYTREE_SHARE} \* ${PYTHONPREFIX_SITELIBDIR}/${PORTNAME})
	${INSTALL_SCRIPT} ${WRKDIR}/${PORTNAME}.sh ${PREFIX}/bin/${PORTNAME}

.include <bsd.port.mk>
