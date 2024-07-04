# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2023 Luca Barbato

include $(TOPDIR)/rules.mk

PKG_NAME:=python-maturin
PKG_VERSION:=1.6.0
PKG_RELEASE:=1

PYPI_NAME:=maturin
PKG_HASH:=b955025c24c8babc808db49e0ff90db8b4b1320dcc16b14eb26132841737230d

PKG_MAINTAINER:=Luca Barbato <lu_zero@luminem.org>
PKG_LICENSE:=Apache-2.0 MIT
PKG_LICENSE_FILES:=license-apache license-mit

HOST_BUILD_DEPENDS:= \
	python3/host \
	python-build/host \
	python-installer/host \
	python-wheel/host \
	python-setuptools-rust/host
HOST_BUILD_PARALLEL:=1
PKG_HOST_ONLY:=1

include $(INCLUDE_DIR)/../feeds/packages/lang/python/pypi.mk
include $(INCLUDE_DIR)/host-build.mk
include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/../feeds/packages/lang/python/python3-package.mk
include $(INCLUDE_DIR)/../feeds/packages/lang/python/python3-host-build.mk

define Package/python3-maturin
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=Build and publish crates as python packages
  DEPENDS:=$(RUST_ARCH_DEPENDS)
  URL:=https://maturin.rs
  BUILDONLY:=1
endef

define Package/python3-maturin/description
  Build and publish crates with pyo3, rust-cpython, cffi and uniffi
  bindings as well as rust binaries as python packages.
endef

define Py3Build/Compile
	$(if $(PYTHON3_PKG_HOST_PIP_INSTALL_ARGS), \
		$(call HostPython3/PipInstall,$(PYTHON3_PKG_HOST_PIP_INSTALL_ARGS)) \
	)
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

$(eval $(call HostBuild))
$(eval $(call Py3Package,python3-maturin))
$(eval $(call BuildPackage,python3-maturin))
$(eval $(call BuildPackage,python3-maturin-src))