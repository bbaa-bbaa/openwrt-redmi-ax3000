#
# Copyright (C) 2021 CZ.NIC, z. s. p. o. (https://www.nic.cz/)
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-typing-extensions
PKG_VERSION:=4.8.0
PKG_RELEASE:=1

PYPI_NAME:=typing-extensions
PYPI_SOURCE_NAME:=typing_extensions
PKG_HASH:=df8e4339e9cb77357558cbdbceca33c303714cf861d1eef15e1070055ae8b7ef

PKG_MAINTAINER:=Jan Pavlinec <jan.pavlinec1@gmail.com>
PKG_LICENSE:=PSF-2.0
PKG_LICENSE_FILES:=LICENSE

HOST_BUILD_DEPENDS:=python3/host python-build/host python-installer/host python-wheel/host

include $(INCLUDE_DIR)/../feeds/packages/lang/python/pypi.mk
include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/host-build.mk
include $(INCLUDE_DIR)/../feeds/packages/lang/python/python3-package.mk
include $(INCLUDE_DIR)/../feeds/packages/lang/python/python3-host-build.mk

define Package/python3-typing-extensions
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=Module with type hints for Python
  URL:=https://github.com/python/typing
  DEPENDS:= \
	+python3-light
endef

define Package/python3-typing-extensions/description
  Backported and Experimental Type Hints for Python.
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
		$(PYTHON3_PKG_BUILD_VARS)\
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
		$(PYTHON3_PKG_INSTALL_VARS)\
	)
endef

Build/Install=$(Py3Build/Install)

$(eval $(call Py3Package,python3-typing-extensions))
$(eval $(call BuildPackage,python3-typing-extensions))
$(eval $(call BuildPackage,python3-typing-extensions-src))
$(eval $(call HostBuild))