# Created by: Antoine Brodin <antoine@FreeBSD.org>
# $FreeBSD$

CATEGORIES=	devel python
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}

COMMENT=	Python bindings for libevtx

LIB_DEPENDS=	evtx:${PORTSDIR}/devel/libevtx

MASTERDIR=	${.CURDIR}/../libevtx
LIBEVTX_SLAVE=	yes
PLIST=		${.CURDIR}/pkg-plist
CONFIGURE_ARGS=	--enable-python
USE_PYTHON=	yes
INSTALL_WRKSRC=	${WRKSRC}/pyevtx

OPTIONS_DEFINE=	EXAMPLES

EXAMPLESDIR=	${LOCALBASE}/share/examples/py-libevtx
EXAMPLESSRC=	pyevtx

.include "${MASTERDIR}/Makefile"
