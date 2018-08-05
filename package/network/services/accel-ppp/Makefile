#
# Copyright (C) 2013-2015 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=accel-ppp
PKG_RELEASE:=1
PKG_VERSION:=12.0

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL=https://github.com/Excalibur201010/accel-ppp.git
PKG_SOURCE_DATE:=2018-06-20
PKG_SOURCE_VERSION:=90dbcb2f03ddb34c6cc9fab6c9d28cb9ab4ec040

PKG_MAINTAINER:=Alex Paraskeva <sim201010@gmail.com>
PKG_LICENSE:=GPL-2.0

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)

#PKG_INSTALL:=1
#PKG_CONFIG_DEPENDS:=CONFIG_PACKAGE_accel-ppp_$(BUILD_VARIANT)_ext_cer_id

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/accel-ppp
  SECTION:=net
  CATEGORY:=Network
  TITLE:=accel-ppp VPN server
  DEPENDS:=+kmod-ipoe +libpcre +libopenssl +libpthread +librt +libatomic
endef

define Package/accel-ppp/description
High performance PPTP/L2TP/PPPoE/IPoE server
endef

CMAKE_OPTIONS += \
    -DBUILD_DRIVER=FALSE \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DCMAKE_BUILD_TYPE=Release \
    -DLOG_PGSQL=FALSE \
    -DSHAPER=TRUE \
    -DRADIUS=TRUE \
    -DNETSNMP=FALSE \
    -DLOG_FILE=TRUE \
    -DLIB_SUFFIX= \

TARGET_CFLAGS += -I$(STAGING_DIR)/opt/include -D_GNU_SOURCE -g -O2 -Wno-incompatible-pointer-types
TARGET_LDFLAGS += -lpthread -latomic

define Package/accel-ppp/install
	$(INSTALL_DIR) \
		$(1)/usr/sbin \
		$(1)/usr/bin \
		$(1)/usr/share/accel-ppp \
		$(1)/usr/share/accel-ppp/radius \
		$(1)/usr/share/accel-ppp/l2tp \
		$(1)/usr/lib/accel-ppp \
		$(1)/etc/init.d \
		$(1)/etc/accel-ppp

	$(INSTALL_BIN) \
		$(PKG_INSTALL_DIR)/usr/sbin/accel-pppd \
		$(1)/usr/sbin/

	$(INSTALL_BIN) \
		$(PKG_INSTALL_DIR)/usr/bin/accel-cmd \
		$(1)/usr/bin/

	$(INSTALL_BIN) \
		$(PKG_INSTALL_DIR)/usr/lib/accel-ppp/libauth_chap_md5.so \
		$(PKG_INSTALL_DIR)/usr/lib/accel-ppp/libauth_pap.so \
		$(PKG_INSTALL_DIR)/usr/lib/accel-ppp/libipoe.so \
		$(PKG_INSTALL_DIR)/usr/lib/accel-ppp/libipv6_nd.so \
		$(PKG_INSTALL_DIR)/usr/lib/accel-ppp/liblog_syslog.so \
		$(PKG_INSTALL_DIR)/usr/lib/accel-ppp/libpppd_compat.so \
		$(PKG_INSTALL_DIR)/usr/lib/accel-ppp/libradius.so \
		$(PKG_INSTALL_DIR)/usr/lib/accel-ppp/libvlan-mon.so \
		$(PKG_INSTALL_DIR)/usr/lib/accel-ppp/libauth_mschap_v1.so \
		$(PKG_INSTALL_DIR)/usr/lib/accel-ppp/libchap-secrets.so \
		$(PKG_INSTALL_DIR)/usr/lib/accel-ppp/libippool.so \
		$(PKG_INSTALL_DIR)/usr/lib/accel-ppp/libipv6pool.so \
		$(PKG_INSTALL_DIR)/usr/lib/accel-ppp/liblog_tcp.so \
		$(PKG_INSTALL_DIR)/usr/lib/accel-ppp/libpppoe.so \
		$(PKG_INSTALL_DIR)/usr/lib/accel-ppp/libsigchld.so \
		$(PKG_INSTALL_DIR)/usr/lib/accel-ppp/libauth_mschap_v2.so \
		$(PKG_INSTALL_DIR)/usr/lib/accel-ppp/libconnlimit.so \
		$(PKG_INSTALL_DIR)/usr/lib/accel-ppp/libipv6_dhcp.so \
		$(PKG_INSTALL_DIR)/usr/lib/accel-ppp/libl2tp.so \
		$(PKG_INSTALL_DIR)/usr/lib/accel-ppp/liblogwtmp.so \
		$(PKG_INSTALL_DIR)/usr/lib/accel-ppp/libpptp.so \
		$(PKG_INSTALL_DIR)/usr/lib/accel-ppp/libshaper.so \
		$(PKG_INSTALL_DIR)/usr/lib/accel-ppp/liblog_file.so \
		$(1)/usr/lib/accel-ppp/

	$(INSTALL_BIN) \
		$(PKG_INSTALL_DIR)/usr/lib/accel-ppp/libtriton.so \
		$(1)/usr/lib/

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/accel-ppp/radius/dictionary \
		$(PKG_INSTALL_DIR)/usr/share/accel-ppp/radius/dictionary.dhcp \
		$(PKG_INSTALL_DIR)/usr/share/accel-ppp/radius/dictionary.rfc2865 \
		$(PKG_INSTALL_DIR)/usr/share/accel-ppp/radius/dictionary.rfc2869 \
		$(PKG_INSTALL_DIR)/usr/share/accel-ppp/radius/dictionary.rfc4072 \
		$(PKG_INSTALL_DIR)/usr/share/accel-ppp/radius/dictionary.rfc4818 \
		$(PKG_INSTALL_DIR)/usr/share/accel-ppp/radius/dictionary.alcatel \
		$(PKG_INSTALL_DIR)/usr/share/accel-ppp/radius/dictionary.rfc2866 \
		$(PKG_INSTALL_DIR)/usr/share/accel-ppp/radius/dictionary.rfc3162 \
		$(PKG_INSTALL_DIR)/usr/share/accel-ppp/radius/dictionary.rfc4372 \
		$(PKG_INSTALL_DIR)/usr/share/accel-ppp/radius/dictionary.rfc4849 \
		$(PKG_INSTALL_DIR)/usr/share/accel-ppp/radius/dictionary.cisco \
		$(PKG_INSTALL_DIR)/usr/share/accel-ppp/radius/dictionary.rfc2867 \
		$(PKG_INSTALL_DIR)/usr/share/accel-ppp/radius/dictionary.rfc3576 \
		$(PKG_INSTALL_DIR)/usr/share/accel-ppp/radius/dictionary.rfc4675 \
		$(PKG_INSTALL_DIR)/usr/share/accel-ppp/radius/dictionary.rfc5176 \
		$(PKG_INSTALL_DIR)/usr/share/accel-ppp/radius/dictionary.microsoft \
		$(PKG_INSTALL_DIR)/usr/share/accel-ppp/radius/dictionary.rfc2868 \
		$(PKG_INSTALL_DIR)/usr/share/accel-ppp/radius/dictionary.rfc3580 \
		$(PKG_INSTALL_DIR)/usr/share/accel-ppp/radius/dictionary.rfc4679 \
		$(1)/usr/share/accel-ppp/radius/

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/accel-ppp/l2tp/dictionary \
		$(PKG_INSTALL_DIR)/usr/share/accel-ppp/l2tp/dictionary.rfc2661 \
		$(PKG_INSTALL_DIR)/usr/share/accel-ppp/l2tp/dictionary.rfc3931 \
		$(1)/usr/share/accel-ppp/l2tp/

	$(INSTALL_BIN) \
		files/accel-ppp.init \
		$(1)/etc/init.d/accel-ppp

	$(INSTALL_DATA) \
		files/accel-ppp.conf \
		$(1)/etc/accel-ppp

endef

$(eval $(call BuildPackage,accel-ppp))
