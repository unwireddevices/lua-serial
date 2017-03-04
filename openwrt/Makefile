#
# Copyright (C) 2015 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=lua-serial
PKG_VERSION:=1.0.0
PKG_RELEASE:=1
PKG_MAINTAINER:=Unwired Devices <info@unwds.com>
PKG_LICENSE:=MIT

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/unwireddevices/lua-serial
PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=bd2e35d56ffe79db307341a70a51e3fbc1e698e9
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)

PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/lua-serial
  SUBMENU:=Lua
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=Lua Serial UART Library
  URL:=https://github.com/unwireddevices/lua-serial
  DEPENDS:= +lua
endef

define Package/lua-serial/description
  Serial port communication functions for Lua
endef

CONFIGURE_ARGS += \
	--with-lua-inc=$(STAGING_DIR)/usr/include \
	--with-lua-lib=$(STAGING_DIR)/usr/lib

define Build/Configure
	$(call Build/Configure/Default,--with-linux-headers=$(LINUX_DIR))
endef

define Build/Install
endef

define Package/lua-serial/install
	$(INSTALL_DIR) $(1)/usr/lib/lua
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/build/lin32/_ul_serial.so $(1)/usr/lib/lua/
endef

$(eval $(call BuildPackage,lua-serial))
