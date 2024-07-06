#
# Copyright (C) 2015-2018 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-orjson
PKG_VERSION:=3.9.15
PKG_RELEASE:=1

PYPI_NAME:=orjson
PKG_HASH:=95cae920959d772f30ab36d3b25f83bb0f3be671e986c72ce22f8fa700dae061

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE.txt
PKG_BUILD_DEPENDS:=python-maturin/host
include $(INCLUDE_DIR)/../feeds/packages/lang/python/pypi.mk
include $(INCLUDE_DIR)/package.mk
include ../rust/rust-package.mk
include $(INCLUDE_DIR)/../feeds/packages/lang/python/python3-package.mk

define Package/python3-orjson
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=python-orjson
	DEPENDS:=+python3-light \
	$(RUST_ARCH_DEPENDS)
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
		$(PYTHON3_PKG_BUILD_VARS) $(CARGO_PKG_VARS) PYO3_CROSS_LIB_DIR=$(STAGING_DIR)/usr/lib/ \
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
		$(PYTHON3_PKG_INSTALL_VARS) $(CARGO_PKG_VARS) PYO3_CROSS_LIB_DIR=$(STAGING_DIR)/usr/lib/\
	)
endef

Build/Install=$(Py3Build/Install)

$(eval $(call Py3Package,python3-orjson))
$(eval $(call BuildPackage,python3-orjson))
$(eval $(call BuildPackage,python3-orjson-src))
