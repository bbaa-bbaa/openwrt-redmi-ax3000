#
# Copyright (C) 2015-2018 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-onepush
PKG_VERSION:=0.7.2
PKG_RELEASE:=2

PKG_BUILD_DIR:=$(BUILD_DIR)/onepush-3a1d5880e3b8f1c5191ee28acd828def15fe135d
PKG_SOURCE:=python-onepush-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/y1ndan/onepush/tar.gz/3a1d5880e3b8f1c5191ee28acd828def15fe135d?
PKG_HASH:=1144b4309c02bccca5fb4a0d6650a9e6c5814010ef3d61f25728a79cd5d507ab

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE.txt

include $(INCLUDE_DIR)/../feeds/packages/lang/python/pypi.mk
include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/../feeds/packages/lang/python/python3-package.mk

define Package/python3-onepush
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=python-onepush
endef

$(eval $(call Py3Package,python3-onepush))
$(eval $(call BuildPackage,python3-onepush))
$(eval $(call BuildPackage,python3-onepush-src))
