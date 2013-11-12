PKG_NAME = mono
PKG_VERS = 3.2.8
PKG_EXT = tar.bz2
PKG_DIST_NAME = $(PKG_NAME)-$(PKG_VERS).$(PKG_EXT)
PKG_DIST_SITE = http://download.mono-project.com/sources/mono
PKG_DIR = $(PKG_NAME)-$(PKG_VERS)

DEPENDS = native/$(PKG_NAME)

HOMEPAGE = http://www.mono-project.com/
COMMENT  = .NET for linux... dude
LICENSE  =

GNU_CONFIGURE = 1

PRE_CONFIGURE_TARGET = myPreConfigure

ifneq ($(findstring $(ARCH),bromolow cedarview evansport x86),$(ARCH))
$(error $(ARCH) is not a supported architecture)
endif

POST_INSTALL_TARGET = myPostInstall

include ../../mk/spksrc.cross-cc.mk

MONO_NATIVE_INSTALL = $(WORK_DIR)/../../../native/$(PKG_NAME)/work-native/install

.PHONY: myPreConfigure
myPreConfigure:
	$(RUN) autoreconf

.PHONY: myPostInstall
myPostInstall:
	cp -rna $(MONO_NATIVE_INSTALL)/usr/local/lib/mono $(WORK_DIR)/install/usr/local/lib/
	cp -rna $(MONO_NATIVE_INSTALL)/usr/local/bin/* $(WORK_DIR)/install/usr/local/bin/
	cp -rna $(MONO_NATIVE_INSTALL)/usr/local/etc/mono/* $(WORK_DIR)/install/usr/local/etc/mono/

# native files not wanted. Please suggest a better way to do this.
	rm $(INSTALL_DIR)$(INSTALL_PREFIX)/bin/monograph

