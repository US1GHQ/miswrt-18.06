#
# Copyright (C) 2018 Accel-ppp.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk

PKG_NAME:=kmod-ipoe
PKG_RELEASE:=1.10

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/Excalibur201010/ipoe.git
PKG_SOURCE_DATE:=2018-06-19
PKG_SOURCE_VERSION:=47debc3f03945356496fdc4a4fd64ed67f48d712
#PKG_MIRROR_HASH:=2bd1e9aee6d53a2a140ad5ece6d8eeccbfb8ae8c788e84f9dd946e29abb64010
PKG_MAINTAINER:=Alex Paraskeva <sim201010@gmail.com>

include $(INCLUDE_DIR)/package.mk

define KernelPackage/ipoe
  SUBMENU:=Network Support
  TITLE:=Ipoe driver
  URL:=https://accel-ppp.org
  FILES:=$(PKG_BUILD_DIR)/ipoe.ko
  AUTOLOAD:=$(call AutoLoad,75,ipoe)
#  DEPENDS:=+kmod-ipt-conntrack @!LINUX_3_18
endef

include $(INCLUDE_DIR)/kernel-defaults.mk

define KernelPackage/ipoe/description
  Kernel IPOE driver
endef

define Build/Compile
	$(KERNEL_MAKE) SUBDIRS="$(PKG_BUILD_DIR)" modules
endef

$(eval $(call KernelPackage,ipoe))
