# -*- Makefile -*-
#------------------------------------------------------------
# @file   Makefile.am
# @brief  Makefile.am for PortBase unit test
# @date   $Date: 2007/01/21 06:52:52 $
# @author Noriaki Ando <n-ando@aist.go.jp>
#
# $Id: Makefile.am 1724 2010-01-21 01:32:15Z hakuta $
#
#------------------------------------------------------------

#
# $Log: Makefile.am,v $
# Revision 1.3  2007/01/21 06:52:52  n-ando
# The include search path option order in AM_CPPFLAGS was changed.
#
# Revision 1.2  2007/01/12 14:51:52  n-ando
# Some fixes for distribution control.
#
# Revision 1.1  2006/11/27 08:35:06  n-ando
# TestSuites are devided into each directory.
#
#


AUTOMAKE_OPTIONS = 1.9

IDLC = @IDLC@
IDLFLAGS = @IDL_FLAGS@
LIBS = @LIBS@

AM_CPPFLAGS =                     \
	-I.                       \
	-I$(top_builddir)         \
	-I$(top_builddir)/src/lib/ \
	-I$(top_builddir)/src/lib/rtm/idl \
	-I$(top_builddir)/src/lib/coil/include \
	-I$(top_builddir)/src/lib/rtm \
	-I$(includedir)



AM_LDFLAGS =              \
	-L.               \
	-L$(top_builddir) \
        -L$(top_builddir)/src/lib/coil/lib/ 


IDL_SOURCES =                                \
	$(top_srcdir)/src/lib/rtm/idl/RTC.idl        \
	$(top_srcdir)/src/lib/rtm/idl/SDOPackage.idl \
	$(top_srcdir)/src/lib/rtm/idl/OpenRTM.idl \
	$(top_srcdir)/src/lib/rtm/idl/Manager.idl \
	$(top_srcdir)/src/lib/rtm/idl/BasicDataType.idl \
	$(top_srcdir)/src/lib/rtm/idl/DataPort.idl



noinst_PROGRAMS = PortBaseTests

nodist_PortBaseTests_SOURCES =           \
	../TestRunner.cpp                \
	$(IDL_SOURCES:.idl=Skel.cpp)     \
	$(top_srcdir)/src/lib/rtm/NVUtil.cpp \
	$(top_srcdir)/src/lib/coil/common/Properties.cpp \
	$(top_builddir)/src/lib/rtm/PortBase.cpp \
	$(top_srcdir)/src/lib/rtm/SystemLogger.cpp           \
	$(top_srcdir)/src/lib/rtm/Manager.cpp         \
	$(top_srcdir)/src/lib/rtm/NamingManager.cpp   \
	$(top_srcdir)/src/lib/rtm/CorbaNaming.cpp     \
	$(top_srcdir)/src/lib/rtm/CorbaPort.cpp          \
	$(top_srcdir)/src/lib/rtm/ConnectorListener.cpp  \
	$(top_srcdir)/src/lib/rtm/CORBA_IORUtil.cpp      \
	$(top_srcdir)/src/lib/rtm/ManagerConfig.cpp   \
	$(top_srcdir)/src/lib/rtm/ModuleManager.cpp   \
	$(top_srcdir)/src/lib/rtm/ManagerServant.cpp  \
	$(top_srcdir)/src/lib/rtm/RTObject.cpp     \
	$(top_builddir)/src/lib/rtm/PortAdmin.cpp  \
	$(top_srcdir)/src/lib/rtm/ConfigAdmin.cpp  \
	$(top_srcdir)/src/lib/rtm/FactoryInit.cpp              \
	$(top_srcdir)/src/lib/rtm/CdrRingBuffer.cpp            \
	$(top_srcdir)/src/lib/rtm/DefaultPeriodicTask.cpp      \
	$(top_srcdir)/src/lib/rtm/PublisherFlush.cpp           \
	$(top_srcdir)/src/lib/rtm/PublisherNew.cpp             \
	$(top_srcdir)/src/lib/rtm/PublisherPeriodic.cpp        \
	$(top_srcdir)/src/lib/rtm/InPortCorbaCdrProvider.cpp   \
	$(top_srcdir)/src/lib/rtm/InPortCorbaCdrConsumer.cpp   \
	$(top_srcdir)/src/lib/rtm/OutPortCorbaCdrConsumer.cpp  \
	$(top_srcdir)/src/lib/rtm/OutPortCorbaCdrProvider.cpp  \
	$(top_srcdir)/src/lib/rtm/ExtTrigExecutionContext.cpp    \
	$(top_srcdir)/src/lib/rtm/PeriodicExecutionContext.cpp   \
	$(top_srcdir)/src/lib/rtm/OpenHRPExecutionContext.cpp    \
	$(top_srcdir)/src/lib/rtm/PeriodicECSharedComposite.cpp  \
	$(top_srcdir)/src/lib/rtm/Factory.cpp         \
	$(top_srcdir)/src/lib/rtm/ECFactory.cpp       \
	$(top_srcdir)/src/lib/rtm/NumberingPolicy.cpp \
	$(top_srcdir)/src/lib/rtm/OutPortBase.cpp                \
	$(top_srcdir)/src/lib/rtm/OutPortProvider.cpp            \
	$(top_srcdir)/src/lib/rtm/OutPortConnector.cpp           \
	$(top_srcdir)/src/lib/rtm/OutPortPullConnector.cpp       \
	$(top_srcdir)/src/lib/rtm/OutPortPushConnector.cpp       \
	$(top_srcdir)/src/lib/rtm/InPortBase.cpp                 \
	$(top_srcdir)/src/lib/rtm/InPortProvider.cpp             \
	$(top_srcdir)/src/lib/rtm/InPortConnector.cpp            \
	$(top_srcdir)/src/lib/rtm/InPortPullConnector.cpp        \
	$(top_srcdir)/src/lib/rtm/InPortPushConnector.cpp        \
	$(top_srcdir)/src/lib/rtm/SdoConfiguration.cpp \
	$(top_srcdir)/src/lib/rtm/SdoOrganization.cpp  \
	PortBaseTests.cpp


PortBaseTests_LDFLAGS = -L$(libdir) $(AM_LDFLAGS)
PortBaseTests_LDADD   = -lcppunit -lcoil -luuid

EXTRA_DIST =          \
	PortBaseTests.cpp

# all
all: do-test

# do tests
do-test:
	./PortBaseTests --xml portbasetests.xml \
	--xsl default.xsl

# clean-up
clean-local:
	rm -f                               \
        *.log *.xml                         \
	*.o *.Po *.gch *.la                 \
	*Skel.cpp *Skel.h *Stub.cpp *Stub.h \
	*~ *core                            \
	Makefile.old                        \
	*.cc *.hh *.i *.a *.c *.inl
