#
# Copyright (c) 2014 Arduino LLC. All right reserved.
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=luci-app-arduino-webpanel
PKG_VERSION:=1.5.7
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=http://downloads.arduino.cc/
PKG_MD5SUM:=0bf3aef68fc153ff7ee5c196f8fa1e24

include $(INCLUDE_DIR)/package.mk

define Package/luci-app-arduino-webpanel
  SECTION:=luci
  CATEGORY:=LuCI
  SUBMENU:=3. Applications
  TITLE:= simplified wifi configuration panel
  DEPENDS:=+luci +luci-lib-json +uhttpd-mod-lua +yun-scripts
endef

define Package/luci-app-arduino-webpanel/description
	simplified wifi configuration panel
endef

define Build/Compile
	# NOOP
endef

define Package/luci-app-arduino-webpanel/install
	$(INSTALL_DIR) $(1)/usr/lib/lua/luci/controller/arduino
	$(INSTALL_DIR) $(1)/usr/lib/lua/luci/view/arduino
	$(INSTALL_DIR) $(1)/www/luci-static/resources/arduino

	find $(PKG_BUILD_DIR)/usr/ -name '*.lua' -exec luac -s -o {} {} \;
	$(CP) $(PKG_BUILD_DIR)/usr/* $(1)/usr/
	$(CP) $(PKG_BUILD_DIR)/www/* $(1)/www/
endef

$(eval $(call BuildPackage,luci-app-arduino-webpanel))

