!if "$(CPU)" == "i386" && "$(TARGETOS)" == "WINNT" && ("$(APPVER)" == "5.01")

INCLUDE=$(MSSDK)\include\prerelease;$(INCLUDE)
LIB=$(MSSDK)\lib\prerelease;$(LIB)

#----- Include the PSDK's WIN32.MAK to pick up defines-------------------
!include <win32.mak>

PROJ = PlayWnd
all:    $(OUTDIR) $(OUTDIR)\$(PROJ).exe

$(OUTDIR):
     if not exist "$(OUTDIR)/$(NULL)" mkdir "$(OUTDIR)"

EXTRA_LIBS = msvcrtd.lib strmiids.lib olepro32.lib msacm32.lib winmm.lib msvcrt.lib quartz.lib odbccp32.lib odbc32.lib shell32.lib advapi32.lib

LINK32_OBJS = $(OUTDIR)\playwnd.obj \
              $(OUTDIR)\playwnd.res

.cpp{$(OUTDIR)}.obj:
     $(cc) $(cflags) $(cdebug) $(cvarsdll) /GX /D_MBCS /I"..\..\BaseClasses" /I"..\..\..\..\..\include" /Fo"$(OUTDIR)\\" /Fd"$(OUTDIR)\\" $**

$(OUTDIR)\playwnd.res:
     $(rc) $(rcflags) $(rcvars) /Fo$(OUTDIR)\playwnd.res playwnd.rc

$(OUTDIR)\$(PROJ).exe:   $(LINK32_OBJS)
     $(link) $(ldebug) $(guilflags) /MACHINE:$(CPU) /PDB:$(OUTDIR)\$(PROJ).pdb -out:$(OUTDIR)\$(PROJ).exe $(LINK32_OBJS) $(EXTRA_LIBS) $(baselibs) $(olelibs) 

clean:
     $(CLEANUP)
!else
!message This sample is targeted to build for Windows XP 32-only using this makefile.
!endif