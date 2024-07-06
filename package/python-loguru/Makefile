#
# Copyright (C) 2015-2018 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-loguru
PKG_VERSION:=0.7.2
PKG_RELEASE:=1

PYPI_NAME:=loguru
PKG_HASH:=e671a53522515f34fd406340ee968cb9ecafbc4b36c679da03c18fd8d0bd51ac

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE.txt

include $(INCLUDE_DIR)/../feeds/packages/lang/python/pypi.mk
include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/../feeds/packages/lang/python/python3-package.mk

define Package/python3-loguru
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=python-loguru
endef


$(eval $(call Py3Package,python3-loguru))
$(eval $(call BuildPackage,python3-loguru))
$(eval $(call BuildPackage,python3-loguru-src))
