TOP=../..
include $(TOP)/configure/CONFIG
#----------------------------------------
#  ADD MACRO DEFINITIONS AFTER THIS LINE

# The following gets rid of the -fno-implicit-templates flag on vxWorks, 
# so we get automatic template instantiation.
# This is what we want for miscellaneous/asynPortDriver.cpp
ifeq (vxWorks,$(findstring vxWorks, $(T_A)))
CODE_CXXFLAGS=
endif

PROD_NAME = simDetectorApp
PROD_IOC = $(PROD_NAME)

# <name>.dbd will be created from <name>Include.dbd
DBD += $(PROD_NAME).dbd
$(PROD_NAME)_DBD += simDetectorSupport.dbd
$(PROD_NAME)_DBD += caPutLog.dbd  # For standard format
$(PROD_NAME)_DBD += caPutJsonLog.dbd  # For JSON format (Exists only if module is compiled with supported version of base)

# <name>_registerRecordDeviceDriver.cpp will be created from <name>.dbd
PROD_SRCS_DEFAULT += $(PROD_NAME)_registerRecordDeviceDriver.cpp $(PROD_NAME)Main.cpp
PROD_SRCS_vxWorks += $(PROD_NAME)_registerRecordDeviceDriver.cpp

PROD_LIBS += simDetector

$(PROD_NAME)_LIBS += caPutLog  # Required for both output formats

include $(ADCORE)/ADApp/commonDriverMakefile

#=============================

include $(TOP)/configure/RULES
#----------------------------------------
#  ADD RULES AFTER THIS LINE

