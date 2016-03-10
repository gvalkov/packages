#
# Copyright (C) 2016 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-evdev
PKG_VERSION:=0.6.0
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://pypi.python.org/packages/source/e/evdev
PKG_MD5SUM:=294ac2997bd419d56b9451511536f9f4

PKG_BUILD_DEPENDS:=python python-setuptools
PKG_LICENSE:=BSD-3-Clause
PKG_LICENSE_FILES:=LICENSE

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python-package.mk)

define Package/python-evdev
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=python-evdev
  URL:=python-evdev.readthedocs.org/en/latest
  DEPENDS:=+python-light
endef

define Package/python-evdev/description
Python bindings to the Linux input subsystem.
endef

define Build/Compile
	$(SED) -i 's|/usr/include/linux/|$(LINUX_DIR)/|' setup.py
	$(call Build/Compile/PyMod,,install --prefix=/usr --root=$(PKG_INSTALL_DIR))
endef

define Package/python-evdev/install
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)
	$(CP) $(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* $(1)$(PYTHON_PKG_DIR)
endef

$(eval $(call PyPackage,python-evdev))
$(eval $(call BuildPackage,python-evdev))
