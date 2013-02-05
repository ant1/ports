# Created by: Pieter Danhieux <opr@bsdaemon.be>
# $FreeBSD$

PORTNAME=	sleuthkit
PORTVERSION=	4.0.2
CATEGORIES=	sysutils security
MASTER_SITES=	SF

MAINTAINER=	antoine@FreeBSD.org
COMMENT=	Tools and library for filesystem forensic analysis

RUN_DEPENDS=	p5-DateTime-TimeZone>=0:${PORTSDIR}/devel/p5-DateTime-TimeZone \
		exif:${PORTSDIR}/graphics/exif

CONFLICTS=	ja-ls-[0-9]*

GNU_CONFIGURE=	yes
USE_PERL5=	yes
USE_LDCONFIG=	yes
DATADIR=	${PREFIX}/share/tsk3
CPPFLAGS+=	-I${LOCALBASE}/include

PORTDOCS=	NEWS.txt README.txt
MAN1=		blkcalc.1 blkcat.1 blkls.1 \
		blkstat.1 ffind.1 fls.1 fsstat.1 hfind.1 icat.1 ifind.1 \
		ils.1 img_cat.1 img_stat.1 istat.1 jcat.1 jls.1 mactime.1 \
		mmls.1 mmstat.1 mmcat.1 sigfind.1 sorter.1 \
		tsk_comparedir.1 tsk_gettimes.1 tsk_loaddb.1 tsk_recover.1

OPTIONS_DEFINE=	DOCS LIBEWF JAVA
LIBEWF_DESC=	Build with EWF support
OPTIONS_DEFAULT=LIBEWF JAVA

.include <bsd.port.options.mk>

.if ${PORT_OPTIONS:MLIBEWF}
LIB_DEPENDS+=		ewf:${PORTSDIR}/devel/libewf
CONFIGURE_ARGS+=	--with-libewf=${LOCALBASE}
.else
CONFIGURE_ARGS+=	--without-libewf
.endif

.if ${PORT_OPTIONS:MJAVA}
CATEGORIES+=	java
#BUILD_DEPENDS+=	ant:${PORTSDIR}/devel/apache-ant
USE_JAVA=	yes
PLIST_SUB+=	JAVA=""
CONFIGURE_ENV+=	_ACJNI_JAVAC="${JAVAC}"
.else
PLIST_SUB+=	JAVA="@comment "
.endif

post-patch:
.if ${PORT_OPTIONS:MJAVA}
	${REINPLACE_CMD} -e '/bsdi\*/ { h; s|bsdi|freebsd| ; s|bsdos|freebsd| ; G; }' ${WRKSRC}/configure
#	${REINPLACE_CMD} -e 's|depends="init-ivy, compile"|depends="compile"|' \
#		-e '/antcall target="retrieve-deps"/d' ${WRKSRC}/bindings/java/build.xml
.endif

#post-build:
#.if ${PORT_OPTIONS:MJAVA}
#	cd ${WRKSRC}/bindings/java && ant
#.endif

post-install:
.if ${PORT_OPTIONS:MDOCS}
	@${MKDIR} ${DOCSDIR}
	cd ${WRKSRC} && ${INSTALL_DATA} ${PORTDOCS} ${DOCSDIR}
.endif
#.if ${PORT_OPTIONS:MJAVA}
#	${INSTALL_DATA} ${WRKSRC}/bindings/java/dist/Tsk_DataModel.jar ${JAVAJARDIR}/Tsk_DataModel.jar
#.endif

.include <bsd.port.mk>
