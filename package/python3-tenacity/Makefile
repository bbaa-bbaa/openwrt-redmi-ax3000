#
# Copyright (C) 2015-2018 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-tenacity
PKG_VERSION:=8.2.3
PKG_RELEASE:=1

PYPI_NAME:=tenacity
PKG_HASH:=5398ef0d78e63f40007c1fb4c0bff96e1911394d2fa8d194f77619c05ff6cc8a

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE.txt

include $(INCLUDE_DIR)/../feeds/packages/lang/python/pypi.mk
include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/../feeds/packages/lang/python/python3-package.mk

define Package/python3-tenacity
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=python-tenacity
endef


$(eval $(call Py3Package,python3-tenacity))
$(eval $(call BuildPackage,python3-tenacity))
$(eval $(call BuildPackage,python3-tenacity-src))
