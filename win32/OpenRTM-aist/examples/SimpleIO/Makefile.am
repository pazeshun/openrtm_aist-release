## -*- Makefile -*-
##---------------------------------------------------------------------------
## Makefile.am for win32/OpenRTM-aist/examples/SimpleIO
##
## $Id: Makefile.am 2289 2012-02-03 02:33:33Z kurihara $
##---------------------------------------------------------------------------
clean-local:
	rm -rf Debug Release
	rm -rf *~ *.cpp *.h *.idl rtc.conf
	rm -rf *.vcproj *.vcxproj *.user *.ncb *.suo
	rm -rf ConsoleIn ConsoleInComp ConsoleOut ConsoleOutComp

src:
	cp -p $(top_srcdir)/examples/SimpleIO/*.cpp .
	cp -p $(top_srcdir)/examples/SimpleIO/*.h .
	cp -p $(top_srcdir)/examples/SimpleIO/rtc.conf .
	qkc -O- -ms *.cpp
	qkc -O- -ms *.h

dist-hook: src
