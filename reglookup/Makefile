# New ports collection makefile for:	reglookup
# Date created:				9 December 2012
# Whom:					antoine@FreeBSD.org
#
# $FreeBSD$
#

PORTNAME=	reglookup
PORTVERSION=	1.0.1
CATEGORIES=	devel
MASTER_SITES=	GOOGLE_CODE
DISTNAME=	${PORTNAME}-src-${PORTVERSION}

MAINTAINER=	antoine@FreeBSD.org
COMMENT=	Command line utility for reading and querying Windows registries

LICENSE=	GPLv3

LIB_DEPENDS=	talloc:${PORTSDIR}/devel/talloc

USE_ICONV=	yes
USE_LDCONFIG=	yes
USE_PYTHON=	yes
USE_SCONS=	yes
INSTALLS_EGGINFO=yes
PYDISTUTILS_PKGNAME=pyregfi
PYDISTUTILS_PKGVERSION=1.0
MANCOMPRESSED=	yes

MAN1=		reglookup.1 reglookup-recover.1 reglookup-timeline.1

# XXX Python stuff does not work yet AttributeError: Undefined symbol "winsec_sid2str"

post-patch:
	${REINPLACE_CMD} -e "s|'m'|'iconv', 'm'|" \
		-e "s|env.ManPage(||" -e "s|.1.docbook')|.1.gz'|" \
		-e 's|pyregfi-distutils.py install|pyregfi-distutils.py install -c -O1 --prefix=" + prefix + "|' \
		${WRKSRC}/SConstruct
	${REINPLACE_CMD} -e 's|"libc.so.6"|ctypes.util.find_library("c")|' \
		${WRKSRC}/python/pyregfi/winsec.py

.include <bsd.port.mk>
