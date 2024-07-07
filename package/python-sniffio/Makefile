#
# Copyright (C) 2015-2018 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-sniffio
PKG_VERSION:=1.3.1
PKG_RELEASE:=1

PYPI_NAME:=sniffio
PKG_HASH:=f4324edc670a0f49750a81b895f35c3adb843cca46f0530f79fc1babb23789dc

PKG_LICENSE:=BSD-2-Clause
PKG_LICENSE_FILES:=LICENSE.txt

PKG_BUILD_DEPENDS:=python3/host python-build/host python-hatch-fancy-pypi-readme/host

include $(INCLUDE_DIR)/../feeds/packages/lang/python/pypi.mk
include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/../feeds/packages/lang/python/python3-package.mk

define Package/python3-sniffio
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=python-sniffio
endef

define Py3Build/Compile
	$(call Python3/Run, \
		$(PKG_BUILD_DIR), \
		-m build \
			--no-isolation \
			--outdir "$(PYTHON3_PKG_BUILD_DIR)"/openwrt-build \
			--wheel \
			$(foreach setting,$(PYTHON3_PKG_BUILD_CONFIG_SETTINGS),--config-setting=$(setting)) \
			$(PYTHON3_PKG_BUILD_ARGS) \
			"$(PYTHON3_PKG_BUILD_DIR)" \
			, \
		$(PYTHON3_PKG_BUILD_VARS) \
	)
endef

define Py3Build/Install
	$(call Python3/Run, \
		$(PKG_BUILD_DIR), \
		-m installer \
			--destdir "$(PKG_INSTALL_DIR)" \
			--no-compile-bytecode \
			--prefix /usr \
			"$(PYTHON3_PKG_BUILD_DIR)"/openwrt-build/$(PYTHON3_PKG_WHEEL_NAME)-$(PYTHON3_PKG_WHEEL_VERSION)-*.whl \
			, \
		$(PYTHON3_PKG_INSTALL_VARS) \
	)
endef

Build/Install=$(Py3Build/Install)

$(eval $(call Py3Package,python3-sniffio))
$(eval $(call BuildPackage,python3-sniffio))
$(eval $(call BuildPackage,python3-sniffio-src))
