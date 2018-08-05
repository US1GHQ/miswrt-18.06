include $(TOPDIR)/rules.mk

PKG_NAME:=wireless-regdb

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/Excalibur201010/wireless-regdb
PKG_SOURCE_DATE:=2017-10-20
PKG_SOURCE_VERSION:=87759c4c7940b2dc496543d7be7fef30ac9f8b4a
#PKG_MIRROR_HASH:=5f5b669f32ae36cb65b1d99efbbbfd42c2983cda32f6448346e3e54ffaba3889

PKG_MAINTAINER:=Felix Fietkau <nbd@nbd.name>

include $(INCLUDE_DIR)/package.mk

define Package/wireless-regdb
  SECTION:=firmware
  CATEGORY:=Firmware
  URL:=$(patsubst pub/scm,cgit,$(PKG_SOURCE_URL))
  TITLE:=Wireless Regulatory Database
endef

define Build/Compile
	python $(PKG_BUILD_DIR)/db2fw.py $(PKG_BUILD_DIR)/regulatory.db $(PKG_BUILD_DIR)/db.txt
endef

define Package/wireless-regdb/install
	$(INSTALL_DIR) $(1)/lib/firmware
	$(CP) $(PKG_BUILD_DIR)/regulatory.db $(1)/lib/firmware/
endef

$(eval $(call BuildPackage,wireless-regdb))
