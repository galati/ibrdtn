#
# Copyright (C) 2006 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=ibrdtn
PKG_VERSION_MAJOR:=0
PKG_VERSION_MINOR:=10
PKG_VERSION_MICRO:=0

PKG_VERSION:=$(PKG_VERSION_MAJOR).$(PKG_VERSION_MINOR).$(PKG_VERSION_MICRO)
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=http://www.ibr.cs.tu-bs.de/projects/ibr-dtn/releases

PKG_INSTALL:=1
PKG_FIXUP:=libtool
PKG_BUILD_DEPENDS:=ibrcommon libopenssl zlib

include $(INCLUDE_DIR)/package.mk

define Package/ibrdtn
  SECTION:=libs
  CATEGORY:=Libraries
  DEPENDS:=+ibrcommon +libopenssl +zlib
  TITLE:=IBR-DTN Library
endef

define Package/ibrdtn/description
 Base library for IBR-DTN daemon and tools.
endef

CONFIGURE_ARGS += \
	--with-dtnsec \
	--with-compression

define Build/InstallDev
	$(INSTALL_DIR) $(1)
	$(CP) $(PKG_INSTALL_DIR)/* $(1)/
endef

define Package/ibrdtn/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/lib$(PKG_NAME){.so,-$(PKG_VERSION_MAJOR).$(PKG_VERSION_MINOR).so.*} $(1)/usr/lib/
endef

$(eval $(call BuildPackage,ibrdtn))
