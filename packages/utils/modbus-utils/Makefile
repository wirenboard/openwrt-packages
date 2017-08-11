# Copyright (C) 2015 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=modbus-utils
PKG_VERSION=1.2.3
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/contactless/modbus-utils.git
PKG_SOURCE_VERSION:=0e8a52c65280a15538544e8ecb71e1724e7d9edf
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz

PKG_LICENSE:=GPL-2.0
PKG_LICENSE_FILES:=

PKG_MAINTAINER:=Evgeny Boger <boger@contactless.ru>

PKG_BUILD_PARALLEL:=1
PKG_BUILD_DEPENDS:=libmodbus
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)
#PKG_INSTALL:=1
include $(INCLUDE_DIR)/package.mk

define Package/modbus-utils
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=Modbus client and server command line tools based on libmodbus
  DEPENDS:=libmodbus
  URL:=https://github.com/contactless/modbus-utils.git
endef

define Package/modbus-utils/description
  Modbus client and server command line tools based on libmodbus
endef

define Build/Configure
endef

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR) \
	        $(TARGET_CONFIGURE_OPTS) CFLAGS="$(TARGET_CFLAGS)" \
	        
endef

define Package/modbus-utils/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/modbus_client/modbus_client $(1)/usr/bin/modbus_client
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/modbus_server/modbus_server $(1)/usr/bin/modbus_server
endef

$(eval $(call BuildPackage,modbus-utils))
