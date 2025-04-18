#FILENAME:	Makefile
#USAGE:		Top Makefile
#Version:	$Revision: #3 $
#Modified By:	$Author: cliftm $
#Last Modified:	$Date: 2015/02/26 $
#NOTES- The "DIRS" order is based on compile time dependencies.
#     - The user must modify SUPPORT and EPICS_BASE for local configuration.
#     - To support multiple configurations, use multiple config* directories
#     - Support modules can be shared between configurations only if
#	dependencies are not violated.  Only the "DIRS" are the target of
#	gnumake.  If this configuration is using a support module built by
#	another configuration, then the	DIRS line for that support module
#       must be commented out (i.e, must begin with a '#').

include RELEASE.local
MASTER_FILES = RELEASE.local

include $(EPICS_BASE)/configure/CONFIG_COMMON

###### 1st Tier Modules - Only Depend on EPICS BASE ######

DIRS += $(AUTOSAVE)
RELEASE_FILES += $(AUTOSAVE)/configure/RELEASE

DIRS += $(SNCSEQ)
RELEASE_FILES += $(SNCSEQ)/configure/RELEASE

DIRS += $(IPAC)
RELEASE_FILES += $(IPAC)/configure/RELEASE

###### 2nd Tier Modules - Only Depend on 1st Tier ########

DIRS += $(SSCAN)
RELEASE_FILES += $(SSCAN)/configure/RELEASE

################### 3rd Tier Modules #####################

DIRS += $(CALC)
RELEASE_FILES += $(CALC)/configure/RELEASE

################### 4th Tier Modules #####################

DIRS += $(ASYN)
RELEASE_FILES += $(ASYN)/configure/RELEASE

################### 5th Tier Modules #####################

DIRS += $(BUSY)
RELEASE_FILES += $(BUSY)/configure/RELEASE

################### 6th Tier Modules #####################

DIRS += $(MOTOR)
RELEASE_FILES += $(MOTOR)/configure/RELEASE

##########################################################

all install clean rebuild inc depends build uninstall release:
	echo SUPPORT=$(SUPPORT)
	echo ' '
	echo EPICS_BASE=$(EPICS_BASE)
	echo ' '
	echo MASTER_FILES=$(MASTER_FILES)
	echo ' '
	echo RELEASE_FILES=$(RELEASE_FILES)
	echo ' '
	$(PERL) makeReleaseConsistent.pl $(SUPPORT) $(EPICS_BASE) $(MASTER_FILES) $(RELEASE_FILES)

# per jba, to support actions normally defined in RULES_TOP 
ACTIONS += uninstall distclean cvsclean realuninstall

include RULES_DIRS

